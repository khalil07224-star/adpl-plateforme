# Plateforme ADPL — première version connectable à Supabase

## Contenu
- `index.html` : interface web responsive, consultation publique et espace administrateur.
- `README.txt` : ce guide.

## Avant utilisation
Cette version n'est pas encore publiée sur Internet et n'est pas encore configurée avec votre projet Supabase.

1. Ouvrir `index.html` dans un navigateur.
2. Dans Supabase, ouvrir **Project Settings → API**.
3. Copier l'URL du projet et la clé **anon / publishable** (jamais `service_role`).
4. Les coller dans la zone « Connexion à la base ADPL » puis enregistrer.
5. Se connecter avec un compte administrateur créé dans Supabase Auth et ajouté à `public.admin_accounts`.

## Hypothèses de structure
Le code suppose les colonnes suivantes :
- `membres`: `id`, `numero_membre`, `nom`, `prenom`, `date_inscription`, `actif`
- `cotisations`: `id`, `membre_id`, `annee`, `mois`, `montant`, `statut`, `reference_paiement`, `date_paiement`
- `admin_accounts` avec `user_id`, `username`, `role`
- fonction RPC `public.is_adpl_admin()` renvoyant un booléen.

Si vos noms de colonnes diffèrent, il faudra ajuster le code ou le schéma SQL avant mise en production.

## Sécurité / confidentialité
La consultation publique est activée selon le choix de transparence retenu : les noms et statuts de cotisation peuvent être visibles sans connexion. Vérifiez que les membres ont été informés de cette publication. Ne mettez jamais la clé `service_role` dans le navigateur. Les suppressions physiques de membres/cotisations ne sont pas proposées dans cette interface pour préserver l'historique financier.

## Limites de cette première version
- Pas encore d'hébergement/publication en ligne.
- Pas encore de paiement direct Orange Money/Wave : les références sont saisies puis vérifiées manuellement.
- La configuration Supabase est enregistrée dans le navigateur utilisé.
- Les administrateurs doivent avoir un compte Auth avec mot de passe valide.

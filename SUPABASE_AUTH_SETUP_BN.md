# BOOYA BD — Supabase Authentication Setup

The registration form now collects full name, mobile number, email, and password. The mobile number is saved in the Supabase Auth user's `user_metadata.phone`; the display name is saved as `user_metadata.username`. This app does not request or verify a phone OTP.

## Required hosted Supabase setting

To prevent confirmation emails / email OTP from being required, turn off **Confirm email** in the hosted Supabase project:

1. Open Supabase Dashboard and select project `zuwtvklxjzuuyuqpghyk`.
2. Open **Authentication → Sign In / Providers → Email** (the label may appear as **Authentication → Providers → Email**).
3. Turn **Confirm email** OFF and save.
4. Test registration with a new email address.

The `supabase/config.toml` in this project also sets `auth.email.enable_confirmations = false` for local Supabase configuration. Editing this file alone does not change the already-hosted project's dashboard setting.

## Important

With email confirmation disabled, anyone can register using an email address they have not proved they own. The mobile number is also not verified because no SMS OTP is used. Do not use email or phone metadata alone as proof of a person's identity.

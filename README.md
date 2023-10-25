# Ansible-Vault
Learn Ansible Vault Deep Dive

### Ansible Vault Introduction
Ansible Vault is a feature in Ansible that allows you to securely store sensitive data, such as passwords, encryption keys, API tokens, and other secrets, within your Ansible playbooks and roles. It helps protect sensitive information from being exposed in plaintext in your code repositories or when shared with others. Ansible Vault uses strong encryption to protect the data, ensuring it remains confidential.

Here's an introduction to Ansible Vault and how to use it:

**1. Encrypting Sensitive Data:**

You can encrypt sensitive data using the `ansible-vault` command. For example, to encrypt a file called `secrets.yml`, you can run:

```bash
ansible-vault encrypt secrets.yml
```

You'll be prompted to enter a password, which you'll need to provide whenever you want to access the encrypted data. It's essential to remember this password or securely manage it.

**2. Editing Encrypted Files:**

To edit an encrypted file, you can use the `edit` subcommand of `ansible-vault`:

```bash
ansible-vault edit secrets.yml
```

This command will prompt you for the decryption password and then open the file in your default text editor.

**3. Decrypting Files:**

To decrypt an encrypted file, you can use the `decrypt` subcommand:

```bash
ansible-vault decrypt secrets.yml
```

You'll need to provide the decryption password to perform this operation.

**4. Running Playbooks with Encrypted Data:**

When you have an Ansible playbook that includes encrypted data, you'll need to provide the decryption password when running the playbook. You can do this using the `--ask-vault-pass` option:

```bash
ansible-playbook playbook.yml --ask-vault-pass
```

Alternatively, you can store the decryption password in a file and provide it using the `--vault-password-file` option:

```bash
ansible-playbook playbook.yml --vault-password-file my_password_file.txt
```

**5. Changing the Vault Password:**

To change the password used for encrypting and decrypting files, you can use the `rekey` subcommand:

```bash
ansible-vault rekey secrets.yml
```

This will prompt you for the old password and then ask you to set a new one.

**6. Managing Multiple Vault Passwords:**

If you're working with multiple encrypted files and have different passwords for them, you can specify the password for each file using the `--vault-id` option. This allows you to use different passwords for different vault-encrypted files.

Ansible Vault is a powerful tool for securing sensitive information in your Ansible projects. When used correctly, it ensures that your secrets are protected and can be safely stored alongside your code. However, remember to handle password management and storage securely, as losing the password means losing access to the encrypted data.

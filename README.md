# NPK - Increase your cred yield!

NPK is a distributed hash-cracking platform built entirely of serverless components in AWS including Cognito, DynamoDB, and S3. It was designed for easy deployment and the intuitive UI brings high-power hash-cracking to everyone.

Changes from the source repo:
- added support for g6e instances
- fixed g4ad vcpu/quota cost
- wordlist compression pipeline fixes

![dashboard_progress](docs/img/dashboard_progress.png)

'NPK' is an initialism for the three primary atomic elements in fertilizer (Nitrogen, Phosphorus, and Potassium). Add it to your hashes to increase your cred yield!

## How it works

Let's face it - even the beastliest cracking rig spends a lot of time at idle. You sink a ton of money up front on hardware, then have the electricity bill to deal with. NPK lets you leverage extremely powerful hash cracking with the 'pay-as-you-go' benefits of AWS. For example, you can crank out 336 GH/s of NTLM for a mere $1/hr and scale it however you want. NPK was also designed to fit easily within the free tier while you're not using it! Without the free tier, it'll still cost less than $1 per MONTH to have online!

## Features

### 1. Super easy install

Paste a one-liner into AWS CloudShell. Pretty easy.

```source <(curl https://code.fiendishdrwu.com/npk/cloudshell_install.sh)```

If you'd like to use the `dev` branch to use beta features, use this one-liner instead:

```source <(curl https://code.fiendishdrwu.com/npk/cloudshell_install_dev.sh)```

![cloudshell_oneliner](docs/img/cloudshell_oneliner.png)

There are also [Step-by-step instructions](https://github.com/c6fc/npk/wiki/Step-by-step-Installation) if you want them.

### 2. Intuitive campaign builder

Take the trial-and-error out of complex attack types with the intuitive campaign builder. With a couple clicks you can create advanced campaigns that even advanced Hashcat users would struggle to emulate.

![gpu_families](docs/img/gpu_families.png)

### 3. Campaign price and coverage estimates

Take the guess-work out of your campaigns. See how far you'll get and how much it will cost *before* starting the campaign.

![coverage](docs/img/coverage.png)

### 4. Max price enforcement and runaway instance protection

GPU instances are expensive. Runaway GPU instances are EXTREMELY expensive. NPK will enforce a maximum campaign price limit, and was designed to prevent runaway instances even with a complete failure of the management plane.

### 5. Multi-Tenancy & SAML-based single sign-on

NPK supports multiple users, with strict separation of data, campaigns, and results between each user. It can optionally integrate with SAML-based federated identity providers to enable large teams to use NPK with minimal effort.

![user_administration](docs/img/user_administration.png)

### 6. Data lifecycle management

Configure how long data will stay in NPK with configurable lifecycle durations during installation. Hashfiles and results are automatically removed after this much time to keep things nicely cleaned up.

## Easy Install

**ProTip:** To keep things clean and distinct from other things you may have in AWS, it's STRONGLY recommended that you deploy NPK in a fresh account. You can create a new account easily from the 'Organizations' console in AWS. **By 'STRONGLY recommended', I mean 'seriously don't install this next to other stuff'.**

**Note: If you have an older version of NPK that you deployed without the one-liner, you'll need to destroy it before installing the new version**

1. Log into the AWS Console for the account you want to deploy to.
2. Click the AWS CloudShell button in the top right corner.
![cloudshell_icon](docs/img/cloudshell_icon.png)

3. Paste in the one-liner: `source <(curl https://code.fiendishdrwu.com/npk/cloudshell_install.sh)`
4. Use the wizard to complete the configuration

When the deploy finishes, you'll be dropped to a custom prompt, which indicates that NPK is deployed and CloudShell is connected to it.

![deployed_prompt](docs/img/deployed_prompt.png)

If you said 'no' at the end of the wizard, you can run `npm run deploy` from this prompt to finish the deployment.

See https://github.com/c6fc/npk/wiki/Detailed-NPK-Settings for more details about advanced configurations, or https://github.com/c6fc/npk/wiki/Configuring-SAML-SSO for help configuring SAML SSO.

## Connect to an existing installation

**Note: If you have an older version of NPK that you deployed without the one-liner, you'll need to destroy it before installing the new version**

To connect to an existing NPK installation (which is needed to modify or uninstall NPK), log into the AWS account where NPK resides, click the CloudShell icon, and paste in the one-liner:

```source <(curl https://code.fiendishdrwu.com/npk/cloudshell_install.sh)```

CloudShell will now connect to NPK (which may take a minute or two), after which you'll drop to a new prompt that looks like this:

![deployed_prompt](docs/img/deployed_prompt.png)

You're now connected to your NPK installation. This can be performed by any user in the AWS account with admin rights, and can be performed in any region.

## Modify Install

You can change the settings of an install without losing your existing campaigns. Use the instructions above to connect to your NPK installation, then edit `npk-settings.json` as necessary and run `npm run update`. It's that easy!

```sh
~ $ source <(curl https://code.fiendishdrwu.com/npk/cloudshell_install.sh)
@FiendishDrWu/npk> vim npk-settings.json
< ... change your settings however you need >
@FiendishDrWu/npk> npm run update
```

## Uploading your own dictionaries and rule files

Once NPK has been deployed, administrative users can use the NPK console to upload wordlists and rule files using the 'Dictionary Management' link in the sidebar. NPK supports plain-text and gzipped dictionaries.

![upload_dictionaries](docs/img/upload_dictionaries.png)

## Uninstall

You can completely turn down NPK and delete all of its data from AWS very easily. Just attach your CloudShell to NPK, then run `npm run destroy`:

```sh
~ $ source <(curl https://code.fiendishdrwu.com/npk/cloudshell_install.sh)
@FiendishDrWu/npk> npm run destroy
```

# Official Discord Channel

Have questions, need help, want to contribute or brag about a win? Come hang out on Discord!

[![Official c6fc Discord](https://discordapp.com/api/guilds/825770240309985310/widget.png?style=banner3)](https://discord.gg/w4G5k92czX)

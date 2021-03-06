---
title: "Configure WS-Federation provider for Power Apps portals.  | MicrosoftDocs"
description: "Instructions to configure WS-Federation provider for Power Apps portals."
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: 
ms.date: 10/20/2020
ms.author: sandhan
ms.reviewer: tapanm
---

# Configure WS-Federation provider for portals

A WS-Federation–compliant security token service provider can be added as an identity provider. For example, Azure Active Directory, or single Active Directory Federation Services server. Also, a single [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) namespace can be configured as a set of individual identity providers.

> [!NOTE]
> Changes to the authentication settings [may take a few minutes](../admin/clear-server-side-cache.md#caching-changes-for-portals-with-version-926x-or-later) to reflect on the portal. Restart the portal using the [portal actions](../admin/admin-overview.md) if you want to reflect the changes immediately.

To configure WS-Federation provider:

1. Select [Add provider](use-simplified-authentication-configuration.md#add-configure-or-delete-an-identity-provider) for your portal.

1. Select **Login provider** as **Other**.

1. Select **Protocol** as **WS-Federation**.

1. Enter a provider name.

    ![Provider name](media/authentication/wsfed-provider-name.png "Provider name")

1. Select **Next**.

1. Create the application and configure the settings with your identity provider.

    ![Create WS-Federation application](media/authentication/step-1-wsfed.png "Create WS-Federation application")

1. Enter the following site settings for portal configuration.

    ![Configure WS-Federation site settings](media/authentication/configure-wsfed-site-settings.png "Configure WS-Federation site settings")

    > [!NOTE]
    > Ensure that you review&mdash;and if required, change&mdash;the default values.

    | Name | Description |
    | - | - |
    | Metadata address | The WS-Federation identity provider metadata file location. <br> Example (Azure AD): `https://login.microsoftonline.com/7e6ea6c7-a751-4b0d-bbb0-8cf17fe85dbb/federationmetadata/2007-06/federationmetadata.xml` |
    | Authentication type | The Entity Id value that specifies a globally unique name for the WS-Federation identity provider. <br> Example (Azure AD): `https://login.microsoftonline.com/7e6ea6c7-a751-4b0d-bbb0-8cf17fe85dbb/` |
    | Service provider realm | The portal URL that specifies the service provider realm for the WS-Federation identity provider. <br> Example: `https://contoso-portal.powerappsportals.com/` |
    | Assertion consumer service URL | The portal URL that corresponds to the service provider's endpoint (URL). <br> Example: `https://contoso-portal.powerappsportals.com/signin-wsfederation_1` <br> **Note**: If you're using the default portal URL, you can copy and paste the **Reply URL** as shown in *Create and configure WS-Federation provider* settings. If you're using a custom domain name, enter the URL manually. However, ensure that the value enter here is exactly the same as the **Redirect URI** value for the application in the identity provider configuration (such as Azure portal). |

1. Select **Next**.

1. (Optional) Configure additional settings.

    ![Additional settings](media/authentication/wsfed-site-settings-additional.png "Additional settings")

    | Name | Description
    | - | - |
    | Sign-out reply | The URL to return to (sign-out wreply) once the sign-out is complete. |
    | Valid audiences | Comma-separated list of audience URLs. |
    | Validate audiences | If enabled, the audience will be validated during the token validation. |
    | WHR | The home realm of the identity provider (IdP) to use for authentication. Sets the WS-Federation sign-in request **whr** parameter. If empty, the **whr** parameter isn't included in the request. <br> More information: [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation) |
    | Contact mapping with email | Specify whether the contacts are mapped to a corresponding email. When set to On, a unique contact record is associated with a matching email address, assigning the external identity provider to the contact after a successful user sign-in. |

1. Select **Confirm**.

## Edit WS-Federation provider

To edit a configured WS-Federation provider, see [Edit a provider](use-simplified-authentication-configuration.md#edit-a-provider).

### See also

- [Example: Configure WS-Federation for portals with Azure Active Directory](configure-ws-federation-settings-azure-ad.md)
- [Example: Configure WS-Federation provider for a portal with AD FS](configure-ws-federation-settings.md)

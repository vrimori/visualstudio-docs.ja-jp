---
title: "&lt;compatibleFrameworks&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: bb8c31d37bd37f4e2db8415ef1815caec0ec185a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt;要素 (ClickOnce 配置)
このアプリケーションをインストールして実行できる .NET Framework のバージョンを指定します。  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)はサポートしていません、`compatibleFrameworks`アプリケーション マニフェストを保存するときに要素を使用して、証明書で署名済みの[MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)です。 代わりに [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) を使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `compatibleFrameworks`要素は、配置マニフェストをターゲットとする場合の必要な[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ランタイムによって提供される[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]またはそれ以降。 `compatibleFrameworks`要素は、1 つ以上含まれています。`framework`このアプリケーションを実行できる .NET Framework のバージョンを指定する要素。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ランタイムは、最初に、アプリケーションを実行する使用可能な`framework`この一覧にします。  
  
 次の表に、属性を`compatibleFrameworks`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`S` `upportUrl`|省略可能です。 推奨される互換性のある .NET Framework のバージョンをダウンロードできる URL を指定します。|  
  
## <a name="framework"></a>フレームワーク  
 必ず指定します。 次の表に、属性を`framework`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`targetVersion`|必須です。 対象とする .NET Framework のバージョン番号を指定します。|  
|`profile`|必須です。 対象とする .NET Framework のプロファイルを指定します。|  
|`supportedRuntime`|必須です。 .NET Framework を対象に関連付けられているランタイムのバージョン番号を指定します。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次のコード例は、`compatibleFrameworks`内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 この展開が実行できる、[!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]です。 も実行でき、[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]のスーパー セットであるため、[!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]です。  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェス](../deployment/clickonce-deployment-manifest.md)
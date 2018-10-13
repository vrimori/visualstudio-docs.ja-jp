---
title: '&lt;compatibleFrameworks&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 051fd3eea0ffab2a7c5f088538d7208c8286d1d6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176594"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt;要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このアプリケーションをインストールして実行できる .NET Framework のバージョンを指定します。  
  
> [!NOTE]
>  [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)はサポートしていません、`compatibleFrameworks`アプリケーション マニフェストを保存するときに要素を使用して、証明書で署名済みの[MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)します。 代わりに [Mage.exe](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) を使用する必要があります。  
  
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
 `compatibleFrameworks`配置マニフェストを対象とする要素が必要、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]ランタイムによって提供される[!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]またはそれ以降。 `compatibleFrameworks`要素は、1 つ以上含まれています。`framework`このアプリケーションが実行できる .NET Framework のバージョンを指定する要素。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]ランタイムは、最初に、アプリケーションを実行する使用可能な`framework`この一覧にします。  
  
 次の表に、属性を`compatibleFrameworks`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`S` `upportUrl`|任意。 推奨される互換性のある .NET Framework バージョンをダウンロードできる URL を指定します。|  
  
## <a name="framework"></a>フレームワーク  
 必須。 次の表に、属性を`framework`要素をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`targetVersion`|必須。 ターゲット .NET Framework のバージョン番号を指定します。|  
|`profile`|必須。 ターゲット .NET Framework のプロファイルを指定します。|  
|`supportedRuntime`|必須。 .NET Framework を対象に関連付けられているランタイムのバージョン番号を指定します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>例  
 次のコード例は、`compatibleFrameworks`内の要素を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]配置マニフェスト。 この配置を実行できる、[!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]します。 も実行でき、[!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]のスーパー セットである、[!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]します。  
  
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




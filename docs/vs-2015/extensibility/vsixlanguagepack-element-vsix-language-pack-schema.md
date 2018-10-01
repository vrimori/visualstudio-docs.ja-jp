---
title: VSIXLanguagePack 要素 (VSIX 言語パックのスキーマ) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf8e55e38ecf16577482955c30ea95c5a5980087
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539632"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack 要素 (VSIX 言語パックのスキーマ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[VSIXLanguagePack 要素 (VSIX 言語パックのスキーマ)](https://docs.microsoft.com/visualstudio/extensibility/vsixlanguagepack-element-vsix-language-pack-schema)します。  
  
必須。 VSIX 言語パックのルート要素を提供します。 VSIX 言語パックは、VSIX パッケージのローカライズされたインストール情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`xmlns`|VSIX 言語パックのスキーマが定義されている XML 名前空間。|  
  
## <a name="xmlns-attribute"></a>xmlns 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|必須。 言語パックのスキーマを定義するファイルの場所。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[LocalizedName 要素](../extensibility/localizedname-element-vsix-language-pack-schema.md)|必須。 拡張機能のインストールのローカライズされた名前。|  
|[LocalizedDescription 要素](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|必須。 拡張機能のインストールのローカライズされた説明。|  
|[MoreInfoURL 要素](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|任意。 拡張機能のローカライズされた情報へのリンク。|  
|[License 要素](../extensibility/license-element-vsix-language-pack-schema.md)|任意。 ローカライズされたバージョンの拡張機能のライセンス ファイルのパス。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|スキーマ名|VSIX 言語パックのスキーマ|  
|検証ファイル|VSIXLanguagePackSchema.xsd|  
|空にすることができます。|いいえ|  
  
## <a name="see-also"></a>関連項目  
 [VSX 言語パックのスキーマ リファレンス](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)   
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)


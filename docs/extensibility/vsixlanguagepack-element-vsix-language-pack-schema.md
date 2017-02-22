---
title: "VSIXLanguagePack 要素 (VSIX 言語パックのスキーマ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIXLanguagePack 要素 (VSIX 言語パックのスキーマ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必須です。 VSIX 言語パックのルート要素を提供します。 VSIX 言語パックは、VSIX パッケージのローカライズされたインストール情報を提供します。  
  
## 構文  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`xmlns`|VSIX 言語パックのスキーマが定義されている XML 名前空間。|  
  
## xmlns 属性  
  
|値|説明|  
|-------|--------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|必須です。 言語パックのスキーマを定義するファイルの場所。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[LocalizedName 要素](../extensibility/localizedname-element-vsix-language-pack-schema.md)|必須です。 インストールする拡張機能のローカライズされた名前。|  
|[LocalizedDescription 要素](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|必須です。 インストールする拡張機能のローカライズされた説明。|  
|[詳細情報の Url 要素](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|省略可能です。 拡張機能のローカライズされた情報へのリンク。|  
|[ライセンス要素](../extensibility/license-element-vsix-language-pack-schema.md)|省略可能です。 ローカライズされたバージョンの拡張機能のライセンス ファイルのパス。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|なし||  
  
## 要素情報  
  
|||  
|-|-|  
|名前空間|http:\/\/schemas.microsoft.com\/developer\/vsx\-schema\-lp\/2010|  
|スキーマ名|VSIX 言語パック スキーマ|  
|検証ファイル|VSIXLanguagePackSchema.xsd|  
|空にすることができます。|いいえ|  
  
## 参照  
 [VSX 言語パックのスキーマ リファレンス](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)   
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
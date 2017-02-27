---
title: "LocalizedName 要素 (VSIX 言語パックのスキーマ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# LocalizedName 要素 (VSIX 言語パックのスキーマ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必須です。 インストールする拡張機能のローカライズされた名前。  
  
## 構文  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|なし||  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|なし||  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[VSIX LanguagePack 要素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必須です。 VSIX 言語パックのルート要素を提供します。|  
  
## テキスト値  
 必須です。 ターゲット言語の言語パックの名前。  
  
## 要素情報  
  
|||  
|-|-|  
|名前空間|http:\/\/schemas.microsoft.com\/developer\/vsx\-schema\-lp\/2010|  
|スキーマ名|VSIX 言語パック スキーマ|  
|検証ファイル|VSIXLanguagePackSchema.xsd|  
|空にすることができます。|利用不可|  
  
## 参照  
 [VSX 言語パックのスキーマ リファレンス](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)   
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
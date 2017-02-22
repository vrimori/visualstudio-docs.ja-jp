---
title: "ライセンス要素 (VSIX 言語パックのスキーマ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ライセンス要素 (VSIX 言語パックのスキーマ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

省略可能です。 ローカライズされたバージョンの拡張機能のライセンス ファイルのパス。  
  
## 構文  
  
```  
<License>FilePath\license.txt</License>  
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
 表示されるローカライズされたライセンス ファイルの相対パス。  
  
## 解説  
 場合、 `License` 要素が定義されている、セットアップ中に指定されたライセンス ファイルのテキストを表示し、ユーザーは引き続きライセンスに同意する必要があります。  
  
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
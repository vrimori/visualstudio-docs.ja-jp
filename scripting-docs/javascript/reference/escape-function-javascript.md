---
title: "escape 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "エンコーディング (文字列オブジェクトを)"
  - "Escape メソッド"
  - "16 進数"
  - "String オブジェクト、エンコード"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# escape 関数 (JavaScript)
文字列に含まれる非 ASCII 文字などをエスケープ コード付きの文字に変換します。  使用しないでください。  
  
## 構文  
  
```  
escape(charString)   
```  
  
## 解説  
 必須の `charString` 引数は、エンコードする任意の `String` オブジェクトまたはリテラルです。  
  
 **escape** 関数は、`charstring` のコンテンツを格納する文字列値 \(Unicode 形式\) を返します。  すべての空白、区切り記号、アクセント記号付き文字などの非 ASCII 文字は、`%`*xx* 形式のエンコードで置き換えられます。*xx* は、エンコード対象の文字を表す 16 進数です。  たとえば、空白を指定すると、"%20" という文字列が返されます。  
  
 256 以上の値を持つ文字は **%u** *xxxx* という形式で保存されます。  
  
> [!NOTE]
>  **escape** 関数は、URI \(Uniform Resource Identifier\) のエンコードに使用しないでください。  代わりに、`encodeURI` 関数または `encodeURIComponent` 関数の使用をお勧めします。  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 関数](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [unescape 関数](../../javascript/reference/unescape-function-javascript.md)
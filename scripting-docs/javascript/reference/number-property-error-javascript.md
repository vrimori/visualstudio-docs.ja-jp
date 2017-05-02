---
title: "number プロパティ (Error) (JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number プロパティ"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# number プロパティ (Error) (JavaScript)
特定のエラーに関連付けられている数値を設定または取得します。  `Error` オブジェクトの既定のプロパティは **number** です。  
  
## 構文  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## パラメーター  
 *Object*  
 `Error` オブジェクトの任意のインスタンスを指定します。  
  
 *errorNumber*  
 エラーを表す整数を指定します。  
  
## 解説  
 エラー番号は 32 ビット値です。  上位の 16 ビット ワードは機能識別符号で、下位のワードはエラー コードです。  エラー コードを確認するには、`&` \(ビットごとの And\) 演算子を使用して、number プロパティと 16 進数の `0xFFFF` を組み合わせます。  
  
## 使用例  
 例外をスローさせ、エラー番号から派生したエラー コードを表示する例を次に示します。  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## 使用例  
 このコードによって、次のような出力が生成されます。  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **対象**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## 参照  
 [description プロパティ \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ \(Error\)](../../javascript/reference/name-property-error-javascript.md)
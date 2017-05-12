---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
指定したテキストのデバッグの式を作成します。  
  
## 構文  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### パラメーター  
 `pstrCode`  
 \[入力\]式またはステートメントのテキストを指定します。  
  
 `nRadix`  
 \[入力\]使用する基数。  
  
 `pstrDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号。  `pstrCode` がテキスト ストリームから解析されると、通常ホストは、スクリプト ブロックの末尾を検出する 2 つ単一引用符などの区切り記号を、\(」\) を使用します。  このパラメーターは、使用するホスト区切り記号を指定します。条件付きのプリミティブな前処理を提供するためにスクリプト エンジンができます \(たとえば、単一引用符を「\[入力\]区切り記号として使用する単一引用符を 2 つに置き換えてください。  は、スクリプト エンジンが連携をこの情報は、スクリプト エンジンによって異なります \(および\)。  スクリプト ブロックの末尾を示したためにホストが区切り記号を使用しない場合は `NULL` にこのパラメーターを設定します。  
  
 `dwFlags`  
 \[入力\]次のデバッグのテキストのフラグの組み合わせを設定します:  
  
|定数|値|説明|  
|--------|-------|--------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|テキストがステートメントに対して式であることを示します。  このフラグは、テキストがある言語によって解析方法に影響を与える可能性があります。|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|戻り値が使用できる場合、呼び出し元によって使用されます。|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|副作用はできません。  このフラグが設定されている場合、式の評価は実行時の状態を変更してください。|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|テキストの評価でブレークポイントを許可します。  このフラグが設定されているブレークポイントはテキストの評価時には無視されます。|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|テキストの評価中にエラー レポートを許可します。  このフラグが設定されていないエラーは評価時にホストは報告されません。|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|式を式自体ではなくコード実行コンテキストに評価することを示します。|  
  
 `ppe`  
 \[出力\]指定したテキストのデバッグの式を返します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、指定されたテキストのデバッグの式を作成します。  
  
## 参照  
 [IDebugExpressionContext インターフェイス](../../winscript/reference/idebugexpressioncontext-interface.md)
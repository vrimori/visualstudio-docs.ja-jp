---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
`IDebugDocumentHelper::AddDeferredText` のメソッドによって追加された元のホスト ドキュメントの文字範囲を返します。  
  
## 構文  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### パラメーター  
 `dwTextStartCookie`  
 \[入力\]テキストの開始位置を表すホスト定義されたクッキー。  
  
 `pcharText`  
 \[入力、出力\] A 文字のテキスト バッファー。  このメソッドは、このパラメーターがの場合 `NULL`文字を返しません。  
  
 `pstaTextAttr`  
 \[入力、出力\] A 文字の属性のバッファー。  このメソッドは、このパラメーターがの場合 `NULL`属性を返しません。  
  
 `pcNumChars`  
 \[入力、出力\]返される文字と属性の実際の数を示します。  このパラメーターは、このメソッドを呼び出す前にゼロに設定する必要があります。  
  
 `cMaxChars`  
 \[出力\]に返される文字の最大数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|このメソッドは実装されていません。|  
  
## 解説  
 このメソッドは、ホストが `IDebugDocumentHelper::AddDeferredText`を呼び出す必要 `E_NOTIMPL`を返す場合があります。  
  
> [!NOTE]
>  このメソッドはドキュメントからテキストを返します。  ホストはドキュメントへの編集やそのほかの変更を追跡しません。  
  
## 参照  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)
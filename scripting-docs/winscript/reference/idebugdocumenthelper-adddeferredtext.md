---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
指定したテキストとを使用できますが、文字はありません。ヘルパーに通知します。  
  
## 構文  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### パラメーター  
 `cChars`  
 \[入力\]追加する \(Unicode\) 文字数。  
  
 `dwTextStartCookie`  
 \[入力\]テキストの開始位置を表すホスト定義されたクッキー。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|メソッドが失敗しました。|  
  
## 解説  
 このメソッドは、正確な通知およびサイズ情報を生成するヘルパーが中に必要になるまで追加するためにホストが文字の提供を行うことができます。  `dwTextStartCookie` のパラメーターは、テキストの開始位置を表すホストによって定義されるクッキーです。  `IDebugDocumentText::GetText` 以降のの呼び出しでこのクッキーを提供する必要があります。  たとえば、DBCS のテキストを表すホストに、クッキーはオフセットされたバイトであることができます。  
  
 `IDebugDocumentText::GetText` への単一の呼び出しが複数の呼び出しから `AddDeferredText`に文字を取得できることが前提です。  ヘルパー クラスは、遅延同じ文字の範囲を複数回呼び出す場合があります。  
  
> [!NOTE]
>  `AddDeferredText` の呼び出しは `AddUnicodeText` または `AddDBCSText`の呼び出しと混同しないでください。  この場合、`E_FAIL` が返されます。  
  
## 参照  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)
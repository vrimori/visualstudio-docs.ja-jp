---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロパティの情報が拡張されます。  
  
## 構文  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### パラメーター  
 `guidExtendedInfo`  
 \[入力\] 取得する拡張情報の種類を指定する GUID。  詳細については" 解説 " を参照してください。  
  
 `pExtendedInfo`  
 \[入力\] 拡張プロパティの情報を取得するために使用できる `VARIANT` \(C\+\+\) を返したりまたはオブジェクト \(C\#\)。  たとえばこのパラメーターは [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) のインターフェイスに対して照会できる `IUnknown` のインターフェイスを返すことがあります。  詳細については" 解説 " を参照してください。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  取得する拡張 `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` 情報がない場合はを返します。  
  
## 解説  
 このメソッドは [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) のメソッドを呼び出して取得にある情報を取得するために使用されます。  
  
 次の GUID はその名前がアセンブリでは使用できないためこのメソッドで認識されます \(GUID 値はC\# に指定されます。  追加の GUID は内部で使用するために作成できます。  
  
|名前|GUID|Description|  
|--------|----------|-----------------|  
|guidDocument|{} 3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2|ドキュメントに `IUnknown` のインターフェイスを返します。  通常[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) のインターフェイスは `IUnknown`このインターフェイスから取得できます。|  
|guidCodeContext|{} e2fc65e\-56ce\-11d1\-b528\-00aax004a8797|ドキュメントのコンテキストに `IUnknown` のインターフェイスを返します。  通常[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) のインターフェイスは `IUnknown`このインターフェイスから取得できます。|  
|guidCustomViewerSupported|{} d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c|文字列を通常の式エバリュエーターで実行するカスタム ビューアーの CLSID 返します。|  
|guidExtendedInfoSlot|{} 6df235ad\-82c6\-4292\-9c97\-7389770bc42f|このプロパティがマネージ コードのローカル アドレスを表す 32 ビットのスロット数を表す数値を返します。|  
|guidExtendedInfoSignature|{} b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd|変数の定義にプロパティ オブジェクトに関連付けられた文字列を返します。|  
  
## 参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
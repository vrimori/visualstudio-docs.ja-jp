---
title: "IDebugProperty2::GetExtendedInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetExtendedInfo
helpviewer_keywords: IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7456ebe1e28618270bd90f09186ec49814c62b66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
プロパティの情報を拡張を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidExtendedInfo`  
 [in]取得する拡張情報の種類を決定する GUID です。 詳細については、「解説」を参照してください。  
  
 `pExtendedInfo`  
 [out]返します、 `VARIANT` (C++) またはオブジェクト (c#)、拡張プロパティの情報を取得するために使用できます。 たとえば、このパラメーターを返す可能性があります、`IUnknown`の照会できるインターフェイス、 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)インターフェイスです。 詳細については、「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。 返します`S_GETEXTENDEDINFO_NO_EXTENDEDINFO`を取得する拡張情報がない場合。  
  
## <a name="remarks"></a>コメント  
 このメソッドが適していないを呼び出すことによって取得される情報を取得するために存在、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッドです。  
  
 次の Guid は、(、GUID 値は C# の場合、名前は任意のアセンブリでは使用ではないため)、このメソッドによって通常認識されます。 内部使用のため、追加の Guid を作成できます。  
  
|名前|GUID|説明|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|返します、`IUnknown`ドキュメントへのインターフェイスです。 通常、 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)インターフェイスは、これから取得できる`IUnknown`インターフェイスです。|  
|guidCodeContext|{e2fc65e 56ce-11 d 1-b528-00aax004a8797}|返します、`IUnknown`ドキュメント コンテキストへのインターフェイスです。 通常、 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイスは、これから取得できる`IUnknown`インターフェイスです。|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|通常、式エバリュエーターによって実装され、カスタム ビューアーの CLSID を含む文字列を返します。|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|このプロパティは、マネージ コードのローカル アドレスを表す場合は、必要なスロット数を表す 32 ビットの数値を返します。|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|プロパティのオブジェクトに関連付けられている変数のシグネチャを含む文字列を返します。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
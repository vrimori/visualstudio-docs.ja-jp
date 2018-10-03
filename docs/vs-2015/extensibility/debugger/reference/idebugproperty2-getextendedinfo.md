---
title: IDebugProperty2::GetExtendedInfo |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f98aa625caafa81e4027dbb881c88c0e8d8a8ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535983"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProperty2::GetExtendedInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2-getextendedinfo)します。  
  
拡張プロパティの情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]取得する拡張情報の種類を決定する GUID。 詳細については、「解説」を参照してください。  
  
 `pExtendedInfo`  
 [out]返します、 `VARIANT` (C++) または拡張プロパティの情報を取得するために使用できます (c#) オブジェクト。 たとえば、このパラメーターを返す可能性があります、`IUnknown`インターフェイスのクエリを実行できる、 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)インターフェイス。 詳細については、「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`; エラー コードを返します。 返します`S_GETEXTENDEDINFO_NO_EXTENDEDINFO`を取得する拡張情報がない場合。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出すことによって取得するのには適していません情報を取得するためが存在する、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッド。  
  
 次の Guid は、(GUID 値は、名前は任意のアセンブリで利用できないために c# の指定は) このメソッドによって通常認識されます。 内部使用のため、追加の Guid を作成できます。  
  
|名前|GUID|説明|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|返します、`IUnknown`ドキュメントへのインターフェイス。 通常、 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)インターフェイスは、これから取得できます`IUnknown`インターフェイス。|  
|guidCodeContext|{e2fc65e 56ce-11 d 1-b528-00aax004a8797}|返します、`IUnknown`ドキュメント コンテキストへのインターフェイス。 通常、 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイスは、これから取得できます`IUnknown`インターフェイス。|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|通常、式エバリュエーターによって実装されるカスタム ビューアーの CLSID を格納している文字列を返します。|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|このプロパティは、マネージ コードのローカル アドレスを表す場合は、目的のスロット数を表す 32 ビットの数値を返します。|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|プロパティ オブジェクトに関連付けられている変数のシグネチャを格納している文字列を返します。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)


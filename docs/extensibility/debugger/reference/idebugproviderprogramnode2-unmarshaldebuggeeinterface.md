---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464c840c9f3009c1ed763bdc8dbbf66b8491bfe8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917051"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
プロセスの境界を越えて、指定したインターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `riid`  
 [in]インターフェイスの GUID を取得します。  
  
 `ppvObject`  
 [out]必要なインターフェイスを実装するオブジェクトを返します。 [C++] これは、必要なインターフェイスの型に直接キャストできます。 使用 [c#]、<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>必要なインターフェイスを取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ エンジンがで実行されているときに、このメソッドを使用、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]プロセス領域とデバッグ中のプログラムが、独自のプロセス空間内で実行されています。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
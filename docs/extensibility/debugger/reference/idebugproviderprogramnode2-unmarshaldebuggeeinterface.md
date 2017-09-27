---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1801f2df2dfff7667e8a9991892b3218dc3bb71a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
プロセスの境界を越えて、指定されたインターフェイスを取得します。  
  
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
 [out]必要なインターフェイスを実装するオブジェクトを返します。 [C++] この目的のインターフェイス型に直接キャストできます。 [C#] を使用して、<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>目的のインターフェイスを取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 デバッグ エンジンを実行する場合、このメソッドを使用、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]プロセス空間とデバッグ中のプログラムが、独自のプロセス領域で実行されています。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)

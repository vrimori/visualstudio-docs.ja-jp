---
title: "IDebugDocument2::GetName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocument2::GetName
helpviewer_keywords: IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2eeef7ced30d6f8de3b9d0fc6f783502936a4859
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
いくつかの形式のいずれかで、ドキュメントの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `gnType`  
 [in]値、 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)列挙体を返す名前の型を決定します。  
  
 `pbstrFileName`  
 [out]ドキュメント名を含む文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 タイトル、または、ファイル名またはファイル名の偶数の一部として、このメソッドは、ドキュメントの名前を返すなどのことができます。  
  
## <a name="see-also"></a>参照  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
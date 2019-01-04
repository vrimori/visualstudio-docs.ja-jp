---
title: IDebugProgramPublisher2::PublishProgram |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eeaa86ae2a740a1a31147f7294fd91bdbf5872d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991046"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
この方法は、デバッグ エンジン (DEs) を利用プログラムおよびセッション デバッグ マネージャーになります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Engines`  
 [in]DEs を開始したり、このプログラムにアタッチされる Guid の配列。  
  
 `szFriendlyName`  
 [in]プログラムのフレンドリーな名前（これはメニューまたはユーザーに表示されるダイアログに表示されます）。  
  
 `pDebuggeeInterface`  
 [in]`IUnknown`プログラム インターフェイス (この値は、プログラムを一意に識別するために cookie として使用されますこの同じの値は、プログラムを"非公開"に使用されます)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 プログラムをデバッグに使用できなくするには、呼び出す[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
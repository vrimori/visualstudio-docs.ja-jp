---
title: "IDebugProgramPublisher2::PublishProgram |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 9
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
ms.openlocfilehash: 3f573f35ed0130eb020ac2e8e19a0391050ec06e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
この方法は、デバッグ エンジン (DEs) の利用可能なプログラムとセッションのデバッグ マネージャーになります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Engines`  
 [in]起動したり、このプログラムにアタッチできる DEs の Guid の配列。  
  
 `szFriendlyName`  
 [in](これはメニューや、ユーザーに対して表示されるダイアログ ボックスに表示されます)、プログラムのフレンドリ名。  
  
 `pDebuggeeInterface`  
 [in]`IUnknown`プログラム インターフェイス (この値は、プログラムを一意に識別するクッキーとして使用この同じ値は、プログラムを"取り消す"に使用)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プログラムをデバッグするためには使用できなくするを呼び出す[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)

---
title: IDebugProgramPublisher2::UnpublishProgram |Microsoft Docs
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
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eac934aa599d8b6ac3ff0b8779002620013f246a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533530"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProgramPublisher2::UnpublishProgram](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram)します。  
  
により、プログラムのデバッグを使用できません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDebuggeeInterface`  
 [in]`IUnknown`プログラム インターフェイス。 これは、同じ値に指定された、 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)メソッドが削除されているプログラムを一意に識別して (つまり、される cookie として)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 プログラムで使用できるように、デバッグ エンジンとセッション デバッグ マネージャーを使用して、 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)


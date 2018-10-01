---
title: IDebugField::GetType |Microsoft Docs
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
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af38649a08bc58ae23360110f9b28e23507aa877
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539656"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugField::GetType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfield-gettype)します。  
  
このメソッドは、フィールドの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppType`  
 [out]別のフィールドの型を返します[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)


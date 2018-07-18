---
title: IDebugProgram2::CanDetach |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08387df82b20ef38380fe6302a5ca1f5d0bcbc9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115068"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
デバッグ エンジン (DE) が、プログラムから切り離すことができるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>戻り値  
 場合を返します、デタッチできます`S_OK`、それ以外のエラー コードを返します。 返します`S_FALSE`場合は、DE、プログラムからデタッチすることはできません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
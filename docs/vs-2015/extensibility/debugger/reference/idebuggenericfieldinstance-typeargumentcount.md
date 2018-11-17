---
title: IDebugGenericFieldInstance::TypeArgumentCount |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9b1ee6813394f47574686daa94c23c3dbf1f57c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755462"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインスタンスのパラメーターの引数の型の数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcArgs`  
 [入力、出力]このインスタンスの型パラメーターの引数の数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 たとえば場合、一覧\<int >、このメソッドは、1 を返しますと、一覧\<int, float2 > 2 を返します。 このメソッドは、型引数がない場合に 0 を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)


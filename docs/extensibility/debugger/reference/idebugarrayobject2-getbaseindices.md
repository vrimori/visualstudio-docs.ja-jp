---
title: "IDebugArrayObject2::GetBaseIndices |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
caps.latest.revision: 8
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
ms.openlocfilehash: 3aa9ad51de0f929083457eed86d69cf23f99d10d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
配列の次元数を指定された各インデックスの基本のインデックス (下限) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetBaseIndices (  
   DWORD  dwRank,  
   DWORD* dwIndices  
);  
```  
  
```csharp  
int GetBaseIndices (  
   uint       dwRank,  
   out uint[] dwIndices  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwRank`  
 [in]配列の次元 (rank) の数。  
  
 `dwIndices`  
 [out]配列の基本インデックス (下限) です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 たとえば、この関数に次の c# コードで作成された配列にある ' 5' と返されます。  
  
```  
int[] lengths = { 12 };  
int[] lowerbounds = { 5 };  
Array.CreateInstance(typeof(int), lengths, lowerbounds);  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)

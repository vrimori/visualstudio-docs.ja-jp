---
title: "IDebugArrayObject::GetDimensions |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetDimensions
helpviewer_keywords: IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d516032e458bcc0f85c73c75a9147ff53fc0fff2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
配列の次元を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCount`  
 [in]取得するディメンションの数。  
  
 `dwDimensions`  
 [入力、出力].各次元のサイズが入力配列。 `dwCount`最大サイズを指定します、`dwDimensions`配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 多次元配列の各次元のサイズが異なることができます。 たとえば、3 次元の配列を指定`myarray[3][2][6]`、このメソッドは 3、2、および 6 インチ、`dwDimensions`をこの順序でパラメーター。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
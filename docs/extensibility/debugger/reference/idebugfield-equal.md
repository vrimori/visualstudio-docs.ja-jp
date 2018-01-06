---
title: "IDebugField::Equal |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::Equal
helpviewer_keywords: IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f6cba643f6d1b0f5f1d1c9fff23c8636bd12caca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
このメソッドは、このフィールドと等しいかどうかを指定したフィールドを比較します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pField`  
 [in]この 1 と比較するためのフィールドです。  
  
## <a name="return-value"></a>戻り値  
 フィールドが同じ場合を返します`S_OK`です。 フィールドが異なる場合を返します`S_FALSE.`それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
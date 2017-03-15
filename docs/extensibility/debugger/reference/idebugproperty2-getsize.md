---
title: "IDebugProperty2::GetSize |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 24aeecb4b0fb1b8781ad0cd81b5a562f1b78fc4d
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
プロパティ値のバイト単位のサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwSize`  
 [out]プロパティ値のバイト単位のサイズを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す`S_OK`です。 それ以外の場合エラー コードを返します。 返します。`S_GETSIZE_NO_SIZE`場合は、プロパティのサイズがありません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

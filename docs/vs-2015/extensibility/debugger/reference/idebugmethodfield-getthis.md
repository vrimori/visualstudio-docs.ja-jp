---
title: IDebugMethodField::GetThis |Microsoft Docs
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
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f037798eb29763aea54afc86555171e009d589d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537770"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugMethodField::GetThis](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield-getthis)します。  
  
取得、 `this` (`Me`で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) メソッドを含むオブジェクトのポインター。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppClass`  
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) "this"ポインターを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 オブジェクト指向の言語では通常、クラスの現在のインスタンス化への暗黙のポインターです。 これと呼ばれます`this`(C#)/C++ として`Me`で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)


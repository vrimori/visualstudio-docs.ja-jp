---
title: IDebugFunctionObject::CreatePrimitiveObject |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29bdf57c1d6ab77eeb2e283d13785487911efb5c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767401"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

単純な整数などのプリミティブ データ オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ot`  
 [in]値、 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)を作成するプリミティブの種類を表す列挙体です。  
  
 `ppObject`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)新しく作成されたオブジェクトを表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 によって表される関数のパラメーターであるプリミティブ オブジェクトを表すオブジェクトを作成するには、このメソッドを呼び出して、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイス。 たとえば、式の文字列が"myString(5)"の場合は、このメソッドは 5 の整数を表すオブジェクトを作成する使用は。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)


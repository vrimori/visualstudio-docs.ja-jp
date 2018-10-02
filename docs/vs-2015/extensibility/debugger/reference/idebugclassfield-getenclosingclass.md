---
title: IDebugClassField::GetEnclosingClass |Microsoft Docs
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
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34648ee01b1aaa070dea779777095bda98133211
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534976"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugClassField::GetEnclosingClass](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-getenclosingclass)します。  
  
このクラスの外側のクラスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppClassField`  
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクト、それを囲むを表すクラスします。 外側のクラスが存在しない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このクラスが表されている場合[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクトが入れ子になったクラス、`ppClassField`パラメーターを返します、`IDebugClassField`オブジェクト、それを囲むを表すクラスします。 たとえば、このクラスの定義を考えてみます。  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 呼び出す、`GetEnclosingClass`メソッドを`IDebugClassField`オブジェクトを表す、`NestedClass`クラスを返します、`IDebugClassField`クラスを表すオブジェクト`RootClass`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)


---
title: IDebugGenericParamField |Microsoft Docs
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
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e433d3cde52d51460a9387164239186e47c1b60b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722804"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

マネージ コードのジェネリック型のパラメーターを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 ジェネリックのサポートに使用されます。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|このジェネリック パラメーターに関連付けられている制約の数を返します。|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|このジェネリック パラメーターに関連付けられている制約を取得します。|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|このジェネリック パラメーターのフラグを取得します。|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|このジェネリック パラメーターのインデックスを取得します。|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|このジェネリック パラメーターの名前を取得します。|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|このジェネリック パラメーターの型またはメソッドの所有者を取得します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll


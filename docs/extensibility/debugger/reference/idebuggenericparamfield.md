---
title: IDebugGenericParamField |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4072908a8f6690e3d3b00d8c43690be62083242d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114655"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
マネージ コードのジェネリック型のパラメーターを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 ジェネリックのサポートのために使用します。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|このジェネリック パラメーターに関連付けられている制約の数を返します。|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|このジェネリック パラメーターに関連付けられている制約を取得します。|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|このジェネリック パラメーターのフラグを取得します。|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|このジェネリック パラメーターのインデックスを取得します。|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|このジェネリック パラメーターの名前を取得します。|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|このジェネリック パラメーターの型またはメソッドの所有者を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll
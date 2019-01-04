---
title: IDebugGenericFieldInstance |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9c265591d1836594b9190e031c1bfe3ab5a93813
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990978"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
マネージ コードのジェネリック型のフィールドのインスタンスを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|このインスタンスの型パラメーターの引数を取得します。|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|このインスタンスのパラメーターの引数の型の数を返します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll
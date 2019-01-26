---
title: IDebugDynamicField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53e4bd31833ad5cf3441638c3735230b89a16cf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938455"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
このインターフェイスは、変数の型を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、シンボル プロバイダーによって実行時に判断できる任意の型の基本クラスとして実装されます。 これはマネージ コードのみです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスより専門的なインターフェイスの派生元の基本クラスを表します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 このインターフェイスから継承されたもの以外の任意のメソッドで提供されない`IDebugField`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
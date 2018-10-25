---
title: IDebugPointerObject |Microsoft Docs
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
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4aab9051c8c5ae60ff4a8fa3fb83bc091e3e6f47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197162"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、ポインター オブジェクトを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、ポインター オブジェクトを表すには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスを使用してこのインターフェイスを取得できる[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)場合、`IDebugObject`ポインターを表します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)、`IDebugPointerObject`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|インターフェイスが指すオブジェクトを取得します。|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|インターフェイスの一連の連続するバイトとして指している値を取得します。|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|インターフェイスの一連の連続するバイトを指している値を設定します。|  
  
## <a name="remarks"></a>Remarks  
 式エバリュエーターでは、このインターフェイスを使用して、解析ツリー内のポインターを表します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)


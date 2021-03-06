---
title: IDebugAlias2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 489050b09dde0e0ca43ac4a24cc5951a89bf01e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979791"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 数値のエイリアス、変数を表し、により、式エバリュエーター (EE) アプリケーション ドメインのエイリアスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、マネージ デバッグ エンジン (DE) によって実装されます。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|アプリケーション ドメインの識別子を取得します。|  
  
## <a name="remarks"></a>Remarks  
 エイリアスは、後に、1001 #、# 文字の文字列形式の 10 進数です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll
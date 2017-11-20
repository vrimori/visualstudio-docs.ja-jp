---
title: "IDebugGenericFieldInstance |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d7a0a16a6e7eb9f5901cecb5765d1ea2de2fb98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
マネージ コードのジェネリック型のフィールドのインスタンスを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスでは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|このインスタンスの型パラメーターの引数を取得します。|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|このインスタンスのパラメーターの引数型の数を返します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll
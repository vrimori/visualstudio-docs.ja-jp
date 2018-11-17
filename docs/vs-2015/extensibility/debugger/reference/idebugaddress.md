---
title: IDebugAddress |Microsoft Docs
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
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 82c532434475a46a6bf13a5b2395d6db1799cc15
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743997"
---
# <a name="idebugaddress"></a>IDebugAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、項目のアドレスを表します。 これは、シンボル ハンドラーによって返されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、オブジェクトのアドレスを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 多くのインターフェイスの多くのメソッドは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|取得、 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)オブジェクトとその場所を記述する構造体。|  
  
## <a name="remarks"></a>Remarks  
 シンボル プロバイダーは、オブジェクトと (たとえば、関数、メソッド、またはクラス) の特定のスコープ内での位置を表すには、このインターフェイスを返します。 このインターフェイスがから返され、シンボル プロバイダーと式のさまざまなメソッドに渡されるエバリュエーター。 通常、シンボル プロバイダーは、このインターフェイスの内容を解釈する必要がある唯一のエンティティです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)


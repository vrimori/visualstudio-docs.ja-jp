---
title: IDebugProcessQueryProperties |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542933f414e4ca95da181d26d2cc49c582e553c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535943"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProcessQueryProperties](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessqueryproperties)します。  
  
このインターフェイスによって実装される拡張機能インターフェイスは、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)実装します。 これにより、デバッグ プロセス環境に関する情報を取得する実装者ができます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ プロセスの実行環境に関する情報を取得するには、このインターフェイスを実装します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcessQueryProperties`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|プロパティ値を照会します。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|プロパティの値を照会します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスが実装されていることはほとんどありません。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)


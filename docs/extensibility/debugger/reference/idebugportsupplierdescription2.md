---
title: IDebugPortSupplierDescription2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49ee702c33c322a88c2124b6c6002c5f1fd82d10
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966008"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
により、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]内のテキストを表示する UI、**トランスポート情報**のセクション、**プロセスにアタッチ** ダイアログ ボックス。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、ポートのサプライヤーによって実装されます。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugPortSupplierDescription2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|ポート サプライヤーの説明と記述メタデータを取得します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll
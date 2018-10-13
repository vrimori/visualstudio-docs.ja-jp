---
title: IDebugTypeFieldBuilder |Microsoft Docs
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
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 201f52e6fb49ca3974288c82e0ba74bec0d9caa3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202489"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

型を表すフィールドを作成する機能を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、シンボル プロバイダーから取得されます。  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|プリミティブ型を表すオブジェクトを作成します。|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|指定した型へのポインターを作成します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll


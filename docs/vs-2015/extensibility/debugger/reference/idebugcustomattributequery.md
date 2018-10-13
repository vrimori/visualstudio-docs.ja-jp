---
title: IDebugCustomAttributeQuery |Microsoft Docs
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
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1ffb957f15611562011b7d147a8388f09f11558
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208196"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

メソッドまたは型のカスタム属性のクエリを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|指定した名前のカスタム属性を取得します。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|指定した決定カスタム属性を定義します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll


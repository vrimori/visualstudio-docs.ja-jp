---
title: IDebugGenericFieldDefinition |Microsoft Docs
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
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee253ac5f51e71e1fc58d41fe44a6b76473722c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289658"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

マネージ コードのジェネリック型のフィールドの定義を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|型引数の配列を指定したフィールドのインスタンスを構築します。|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|パラメーターの数を指定された型パラメーターを取得します。|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|[標準] フィールドに関連付けられている型パラメーターの数を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll


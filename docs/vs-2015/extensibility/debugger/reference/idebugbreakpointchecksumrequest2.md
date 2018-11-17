---
title: IDebugBreakpointChecksumRequest2 |Microsoft Docs
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
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0cb4c9de41f53c2bcbf7cc329f5537c2633aa6f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765448"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイント要求のチェックサムをドキュメントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 によって実装される、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]デバッグ パッケージ化とデバッグ エンジンで使用します。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugBreakpointChecksumRequest2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|使用するチェックサム アルゴリズムの一意の識別子を指定されたブレークポイント要求のドキュメントのチェックサムを取得します。|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|このドキュメントのチェックサムが有効になっているかどうかを決定します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll


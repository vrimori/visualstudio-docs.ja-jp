---
title: "IntelliSenseHostFlags |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 36cf7ba40deba4bd133f2c4baf92c310665ed275
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
IntelliSense ホスト フラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|メンバー|説明|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|コンテキスト バッファーは、読み取り専用です。|  
|`IHF_NOSEPARATESUBJECT`|件名のテキストはありません。 コンテキスト バッファーには、IntelliSense のターゲットが含まれています (意味`!IHF_READONLYCONTEXT`)。|  
|`IHF_SINGLELINESUBJECT`|件名のテキストは、マルチ ラインことはできません。|  
|`IHF_FORCECOMMITTOCONTEXT`|`CanCommitIntoReadOnlyBuffer` と同じ。|  
|`IHF_OVERTYPE`|(サブジェクトまたはコンテキスト) での編集は、上書きモードで行う必要があります。|  
  
## <a name="requirements"></a>必要条件  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
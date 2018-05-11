---
title: IntelliSenseHostFlags |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a096e79a64168f74150103a5f3ba3a8683fe184e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
## <a name="requirements"></a>要件  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
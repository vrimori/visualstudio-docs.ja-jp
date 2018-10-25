---
title: IntelliSenseHostFlags |Microsoft Docs
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
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28e78a76c0288cece3c42212a036ff326840b5bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829210"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense のホストのフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
|`IHF_READONLYCONTEXT`|コンテキスト バッファーとは、読み取り専用です。|  
|`IHF_NOSEPARATESUBJECT`|件名テキストはありません。 コンテキスト バッファーには、IntelliSense とターゲットが含まれています (意味`!IHF_READONLYCONTEXT`)。|  
|`IHF_SINGLELINESUBJECT`|件名のテキストは、マルチ ラインことはできません。|  
|`IHF_FORCECOMMITTOCONTEXT`|`CanCommitIntoReadOnlyBuffer` と同じ。|  
|`IHF_OVERTYPE`|編集 (サブジェクトまたはコンテキスト) では、上書きモードで行う必要があります。|  
  
## <a name="requirements"></a>必要条件  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop>


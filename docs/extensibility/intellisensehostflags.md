---
title: "IntelliSenseHostFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "IntelliSense、IntellisenseHostFlags 列挙型"
  - "IntellisenseHostFlags 列挙型"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense のホストのフラグを指定します。  
  
## 構文  
  
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
  
#### パラメーター  
  
|メンバー|説明|  
|----------|--------|  
|`IHF_READONLYCONTEXT`|コンテキスト バッファーとは、読み取り専用です。|  
|`IHF_NOSEPARATESUBJECT`|件名のテキストがありません。 コンテキスト バッファーには、IntelliSense のターゲットが含まれています \(意味 `!IHF_READONLYCONTEXT`\)。|  
|`IHF_SINGLELINESUBJECT`|件名のテキストは、マルチ ラインことはできません。|  
|`IHF_FORCECOMMITTOCONTEXT`|`CanCommitIntoReadOnlyBuffer` と同じ。|  
|`IHF_OVERTYPE`|\(サブジェクトまたはコンテキスト\) での編集は、上書きモードで実行する必要があります。|  
  
## 必要条件  
 SingleFileeditor.idl  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
---
title: "文字列長の制限 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインを文字列長の制限"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 文字列長の制限
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース管理プラグインの API は、さまざまな機能で使用される文字列の長さを制限します。  
  
## 文字列の長さの値  
  
|定数|値|  
|--------|-------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  長さ末尾は含まれません、 `null`です。 "\_LEN"ではなく"\_SIZE"サフィックスを持つ他の定数には、終端の領域は含まれています。 `null`します。  
  
|定数|値|  
|--------|-------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)
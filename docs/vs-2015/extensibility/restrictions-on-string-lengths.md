---
title: 文字列長の制限 |Microsoft Docs
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
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef31cd75fe6221667026bc7af8f9da1e6ac5e4ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790527"
---
# <a name="restrictions-on-string-lengths"></a>文字列長の制限
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ソース管理プラグイン API は、さまざまな関数で使用される文字列の長さを制限します。  
  
## <a name="string-length-values"></a>文字列の長さの値  
  
|定数|[値]|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  長さは、終了は含まれません`null`します。 "_LEN"ではなく"サイズ) (_s"サフィックスを持つその他の定数には、終了するための領域は含ま`null`します。  
  
|定数|[値]|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)


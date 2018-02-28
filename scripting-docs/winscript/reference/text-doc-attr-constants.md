---
title: "TEXT_DOC_ATTR 定数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="textdocattr-constants"></a>TEXT_DOC_ATTR 定数
ドキュメントの属性を記述します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>定数  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|ドキュメントとは、読み取り専用です。|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|ドキュメントは、このドキュメント ツリーのプライマリ ファイルです。|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|ドキュメントは、作業者です。|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|ドキュメントは、スクリプト ファイルです。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
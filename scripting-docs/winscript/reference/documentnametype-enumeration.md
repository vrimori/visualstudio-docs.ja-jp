---
title: DOCUMENTNAMETYPE 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094771"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE 列挙型
ドキュメント用に取得する型を記述します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|アプリケーションのツリーに表示される名前を取得します。|  
|DOCUMENTNAMETYPE_TITLE|ビューアーのタイトル バーに表示される名前を取得します。|  
|DOCUMENTNAMETYPE_FILE_TAIL|パスを持たないファイル名を取得します。|  
|DOCUMENTNAMETYPE_URL|ドキュメントの URL を取得します。|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Id の列挙型が付加されますタイトルを取得します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
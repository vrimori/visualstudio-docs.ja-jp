---
title: "SCRIPTTRACEINFO 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO 列挙型
トレースしているスクリプト イベントを表します。 使用される、 [iactivescriptsitetraceinfo::sendscripttraceinfo メソッド](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>列挙値  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|スクリプトの開始時刻です。|  
|SCRIPTTRACEINFO_SCRIPTEND|スクリプトの終了。|  
|SCRIPTTRACEINFO_COMCALLSTART|COM の呼び出しの開始。|  
|SCRIPTTRACEINFO_COMCALLEND|COM の呼び出しの終了。|  
|SCRIPTTRACEINFO_CREATEOBJSTART|オブジェクトの作成の開始。|  
|SCRIPTTRACEINFO_CREATEOBJEND|オブジェクトの作成の終了。|  
|SCRIPTTRACEINFO_GETOBJSTART|GetObject 呼び出しの開始。|  
|SCRIPTTRACEINFO_GETOBJEND|GetObject 呼び出しの終了。|
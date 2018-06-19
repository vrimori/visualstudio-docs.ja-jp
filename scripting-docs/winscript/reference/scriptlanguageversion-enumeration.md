---
title: SCRIPTLANGUAGEVERSION 列挙型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734072"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 列挙型
可能性のあるバージョンのスクリプトを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>列挙値  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|既定のバージョン。 整数値は 0 です。|  
|SCRIPTLANGUAGEVERSION_5_7|Windows はスクリプト 5.7 です。 整数値は 1 です。|  
|SCRIPTLANGUAGEVERSION_5_8|Windows はスクリプト 5.8 のバージョンです。 整数値は 2 です。|  
|SCRIPTLANGUAGEVERSION_MAX|最大バージョン。 整数値は 255 です。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)
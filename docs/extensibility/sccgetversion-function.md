---
title: "SccGetVersion 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetVersion
helpviewer_keywords: SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2aef7ed21124c2e3555442819461f1989388ab22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetversion-function"></a>SccGetVersion 関数
この関数は、ソース管理プラグインでサポートされているソース管理プラグイン API のバージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 A`LONG`をサポートされているソース管理プラグイン API のバージョン番号を含むデータ型。  
  
|WORD|説明|  
|----------|-----------------|  
|ください|メジャー バージョン|  
|LOWORD|マイナー バージョン|  
  
## <a name="remarks"></a>コメント  
 たとえば、ソース管理プラグインは、ソース管理プラグイン API のバージョン 1.3 をサポートする場合、この関数は 0x0103 に返します。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)
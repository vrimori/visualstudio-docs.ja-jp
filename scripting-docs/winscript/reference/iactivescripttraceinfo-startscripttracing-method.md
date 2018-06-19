---
title: Iactivescripttraceinfo::startscripttracing メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724882"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing メソッド
スクリプト トレースを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSiteTraceInfo`  
 ホストの IActiveScriptSiteTraceInfo へのポインター。  
  
 `guidContextId`  
 コンテキストの GUID です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は次のとおりです。  
  
1.  S_OK: 成功します。  
  
2.  E_POINTER: `pSiteTraceInfo` NULL ポインターです。  
  
3.  E_NOTIMPL: 実装されていません。
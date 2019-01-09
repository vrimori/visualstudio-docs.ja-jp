---
title: Iactivescripttraceinfo::startscripttracing メソッド |Microsoft Docs
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
ms.openlocfilehash: 6462597f55b6b0ceee885d207572e9669a350600
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093643"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing メソッド
スクリプト トレースを開始します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSiteTraceInfo`  
 ホストの IActiveScriptSiteTraceInfo へのポインター。  
  
 `guidContextId`  
 コンテキストの GUID です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値以下のとおりです。  
  
1.  S_OK を返します。成功。  
  
2.  E_POINTER: `pSiteTraceInfo` NULL ポインターです。  
  
3.  E_NOTIMPL:実装されていません。
---
title: StartTrackingContext | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- StartTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1931d8f4e6d9a7e0ed2ddb8d5ca90e580d7166b3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537116"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[StartTrackingContext](https://docs.microsoft.com/visualstudio/msbuild/starttrackingcontext)します。  
  
  
追跡コンテキストを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>パラメーター  
 [入力] `intermediateDirectory`  
 追跡ログを格納するディレクトリ。  
  
 [入力] `taskName`  
 追跡コンテキストを識別します。 この名前はログ ファイル名の作成に使用されます。  
  
## <a name="return-value"></a>戻り値  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) と [SUCCEEDED] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) の追跡コンテキストが作成された場合のビット セット。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** FileTracker.h




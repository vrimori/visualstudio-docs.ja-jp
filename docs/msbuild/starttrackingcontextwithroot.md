---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContextWithRoot
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66065fe94b41c06082e878329a03de3851ee844d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
応答ファイルにルート マーカーを指定し、追跡コンテキストを開始します。  
  
## <a name="syntax"></a>構文  
  
```cpp 
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>パラメーター  
 [入力] `intermediateDirectory`  
 追跡ログを格納するディレクトリ。  
  
 [入力] `taskName`  
 追跡コンテキストを識別します。 この名前はログ ファイル名の作成に使用されます。  
  
 [入力] `rootMarkerResponseFile`  
 ルート マーカーを含む応答ファイルのパス名。 あるコンテキストのすべての追跡をグループ化するためにルート名が使用されます。  
  
## <a name="return-value"></a>戻り値  
 追跡コンテキストが作成された場合、**HRESULT** に **SUCCEEDED** ビットが設定されます。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** FileTracker.h  
  
## <a name="see-also"></a>参照  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
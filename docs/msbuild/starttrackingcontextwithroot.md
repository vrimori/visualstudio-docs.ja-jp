---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da93697f273257d166bf377e9c84b03d59d06f78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
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
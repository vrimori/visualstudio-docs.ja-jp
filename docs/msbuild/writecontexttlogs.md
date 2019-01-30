---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 026fb2dedbfb67aa64c1a8e074e8c4017f9e69aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955805"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
現在のコンテキストのログ ファイルを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>パラメーター  
 [入力] `intermediateDirectory`  
 追跡ログを格納するディレクトリ。  
  
 [入力] `tlogRootName`  
 ログ ファイル名のルート名。  
  
## <a name="return-value"></a>戻り値  
 追跡コンテキストが作成された場合、**HRESULT** に **SUCCEEDED** ビットが設定されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:***FileTracker.h*  
  
## <a name="see-also"></a>関連項目  
 [WriteAllTLogs](../msbuild/writealltlogs.md)
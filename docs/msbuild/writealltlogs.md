---
title: WriteAllTLogs |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ca5bfbdae319aff8d90686deb32a5c7348fa74e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985538"
---
# <a name="writealltlogs"></a>WriteAllTLogs
すべてのスレッドとコンテキストの追跡ログを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)
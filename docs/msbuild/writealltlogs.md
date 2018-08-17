---
title: WriteAllTLogs |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
ms.openlocfilehash: ceec441f6f0110ea514225ed0fab4c4dc2d575bb
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153086"
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
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** *FileTracker.h*  
  
## <a name="see-also"></a>関連項目  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)
---
title: VSG_DEFAULT_RUN_FILENAME |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a05acfd07e8b67bf500864f00ead4d78f2da22ae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922560"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
グラフィックス ログ ファイルの既定のファイル名を定義します。  
  
## <a name="syntax"></a>構文  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>パラメーター  
 `filename`  
 グラフィックス情報がプログラムによってキャプチャされたとき、グラフィックス ログ ファイルに既定で与えられるファイル名。  
  
## <a name="value"></a>[値]  
 グラフィックス ログ ファイルのファイル名を表すリテラル文字列。 既定では、L"default.vsglog" です。  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>コメント  
 プリプロセッサ シンボル `DONT_SAVE_VSGLOG_TO_TEMP` が定義されている場合、ファイル名はキャプチャされるアプリケーションの現在のディレクトリに対する相対パスになるか、または絶対パスです。それ以外の場合は、ユーザーの一時ファイル ディレクトリに対する相対パスになり、絶対パスにすることはできません。  
  
 定義済みのファイル名を変更する必要がありますを再定義する、追加する前に、`vsgcapture.h`プログラムでします。  
  
## <a name="example"></a>例  
 次の例に、キャプチャ ファイルの既定のファイル名を変更する方法を示します。  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>「  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
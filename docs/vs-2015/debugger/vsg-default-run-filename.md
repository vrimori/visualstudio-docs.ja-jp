---
title: VSG_DEFAULT_RUN_FILENAME |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d82052c48444c8c22f205326cfb5ce614ac36aa7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534530"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[VSG_DEFAULT_RUN_FILENAME](https://docs.microsoft.com/visualstudio/debugger/graphics/vsg-default-run-filename)します。  
  
グラフィックス ログ ファイルの既定のファイル名を定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>パラメーター  
 `filename`  
 グラフィックス情報がプログラムによってキャプチャされたとき、グラフィックス ログ ファイルに既定で与えられるファイル名。  
  
## <a name="value"></a>[値]  
 グラフィックス ログ ファイルのファイル名を表すリテラル文字列。 既定では、L"default.vsglog" です。  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Remarks  
 プリプロセッサ シンボル `DONT_SAVE_VSGLOG_TO_TEMP` が定義されている場合、ファイル名はキャプチャされるアプリケーションの現在のディレクトリに対する相対パスになるか、または絶対パスです。それ以外の場合は、ユーザーの一時ファイル ディレクトリに対する相対パスになり、絶対パスにすることはできません。  
  
 定義済みのファイル名を変更する必要がありますを再定義する、追加する前に、`vsgcapture.h`プログラムでします。  
  
## <a name="example"></a>例  
 次の例に、キャプチャ ファイルの既定のファイル名を変更する方法を示します。  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>関連項目  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)




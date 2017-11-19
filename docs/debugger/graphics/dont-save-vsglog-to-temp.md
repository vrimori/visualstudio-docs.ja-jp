---
title: "DONT_SAVE_VSGLOG_TO_TEMP |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 264f67eb9a1fc7f8af739d7eea329de05230c7a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
その存在によって、グラフィックス ログ ファイルがユーザーの一時ファイル ディレクトリに保存されるかどうかを定義します。  
  
## <a name="syntax"></a>構文  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>値  
 その有無によって、グラフィックス ログ ファイルがユーザーの一時ファイル ディレクトリに保存されるかどうかが決まるプリプロセッサ シンボル。 このシンボルが定義されている場合、`VSG_DEFAULT_RUN_FILENAME` で定義されるファイル名は、キャプチャされるアプリケーションの現在のディレクトリに対する相対パスになるか、または絶対パスです。それ以外の場合、`VSG_DEFAULT_RUN_FILENAME` で定義されるファイル名は、ユーザーの一時ファイル ディレクトリに対する相対パスになり、絶対パスにすることはできません。  
  
## <a name="remarks"></a>コメント  
 ユーザーの特権によっては、グラフィック ログ ファイルを任意の場所に保存できないことがあります。 選択した場所にユーザーが書き込むことができるかどうかがわからない場合は、ユーザーの一時ファイル ディレクトリ、または別の既知の場所にグラフィックス ログを保存することをお勧めします。  
  
 定義する必要がありますをグラフィックス ログ ファイルが一時ファイル ディレクトリに保存されていることを防ぐために`DONT_SAVE_VSGLOG_TO_TEMP`インクルードする前に`vsgcapture.h`です。  
  
## <a name="example"></a>例  
 次の例に、グラフィックス ログ ファイルをホスト コンピューターの絶対パスに保存する方法を示します。  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
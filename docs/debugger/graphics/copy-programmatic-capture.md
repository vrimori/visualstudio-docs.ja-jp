---
title: コピー (プログラムによるキャプチャ) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35558a9ad6a4e7d31103910f3fe71c0a12374c22
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042255"
---
# <a name="copy-programmatic-capture"></a>コピー (プログラムによるキャプチャ)
アクティブなグラフィックス ログ (.vsglog) ファイルの内容を、新しいファイルにコピーします。  
  
## <a name="syntax"></a>構文  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szNewVSGLog`  
 新しいグラフィックス ログ ファイルのファイル名。  
  
## <a name="remarks"></a>コメント  
 グラフィックス情報を新しいファイルにコピーするには、グラフィック情報を既にキャプチャしている必要があります。していない場合は、何も実行されません。
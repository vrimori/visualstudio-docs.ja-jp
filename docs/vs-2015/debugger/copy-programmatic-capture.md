---
title: コピー (プログラムによるキャプチャ) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2d6afc3a5693896c17e49ccb07b5152d906d43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776149"
---
# <a name="copy-programmatic-capture"></a>コピー (プログラムによるキャプチャ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アクティブなグラフィックス ログ (.vsglog) ファイルの内容を、新しいファイルにコピーします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szNewVSGLog`  
 新しいグラフィックス ログ ファイルのファイル名。  
  
## <a name="remarks"></a>Remarks  
 グラフィックス情報を新しいファイルにコピーするには、グラフィック情報を既にキャプチャしている必要があります。していない場合は、何も実行されません。




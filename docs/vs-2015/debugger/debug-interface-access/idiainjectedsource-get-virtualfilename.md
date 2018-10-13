---
title: Idiainjectedsource::get_virtualfilename |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: feaf541c8f48247b0379f427aa65669c7afe1e81
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288952"
---
# <a name="idiainjectedsourcegetvirtualfilename"></a>IDiaInjectedSource::get_virtualFilename
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ファイル以外のソース コードに与えられた名前を取得します。挿入されたコードは、します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_virtualFilename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]挿入されたファイル以外のソース コードに与えられた名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)




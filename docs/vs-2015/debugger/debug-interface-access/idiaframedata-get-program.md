---
title: Idiaframedata::get_program |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6daf5262552d056a6ac2d46a092fe94ec7510b15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545279"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiaframedata::get_program](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-program)します。  
  
レジスタの現在の関数を呼び出す前にセットの計算に使用するプログラム文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]プログラムの文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 プログラムの文字列は、プロローグを確立するために解釈されるマクロのシーケンスです。 たとえば、一般的なスタック フレームを使用プログラム文字列`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`します。 形式は、逆ポーランド表記法、演算子がオペランドに従ってください。 `T0` スタック上の一時変数を表します。 この例では、次の手順を実行します。  
  
1.  レジスタの内容を移動`ebp`に`T0`します。  
  
2.  追加`4`の値に`T0`をアドレスを生成、そのアドレスから値を取得およびレジスタに値を格納`eip`します。  
  
3.  格納されているアドレスから値を取得`T0`レジスタに値を格納および`ebp`します。  
  
4.  追加`8`の値に`T0`レジスタに値を格納および`esp`します。  
  
 プログラム文字列が、CPU と現在のスタック フレームで表される関数を設定する呼び出し規約に固有であるに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)




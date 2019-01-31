---
title: Idiaframedata::get_program |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f356dec92e1553eba0b8704f6d456b4d1fb4326f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916343"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
レジスタの現在の関数を呼び出す前にセットの計算に使用するプログラム文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]プログラムの文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プログラムの文字列は、プロローグを確立するために解釈されるマクロのシーケンスです。 たとえば、一般的なスタック フレームを使用プログラム文字列`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`します。 形式は、逆ポーランド表記法、演算子がオペランドに従ってください。 `T0` スタック上の一時変数を表します。 この例では、次の手順を実行します。  
  
1. レジスタの内容を移動`ebp`に`T0`します。  
  
2. 追加`4`の値に`T0`をアドレスを生成、そのアドレスから値を取得およびレジスタに値を格納`eip`します。  
  
3. 格納されているアドレスから値を取得`T0`レジスタに値を格納および`ebp`します。  
  
4. 追加`8`の値に`T0`レジスタに値を格納および`esp`します。  
  
   プログラム文字列が、CPU と現在のスタック フレームで表される関数を設定する呼び出し規約に固有であるに注意してください。  
  
## <a name="see-also"></a>「  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
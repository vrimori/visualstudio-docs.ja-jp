---
title: Vsgdbg::vsgdbg (コンス トラクター) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04f33b117a7ee47fb0c11932c3722f6f2a4a3541
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (コンストラクター)
指定されたブール値パラメーターに基づいて、既定でグラフィックス情報をアクティブにキャプチャして記録するようにグラフィックス診断のアプリ内コンポーネントを準備をするか、または準備しないで、`VsgDbg` クラスのインスタンスを構築します。  
  
## <a name="syntax"></a>構文  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bDefaultInit`  
 グラフィックス情報をアクティブにキャプチャして記録するように、グラフィックス診断のアプリ内コンポーネントを準備することを指定する場合は `true`、この時点ではグラフィックス情報をアクティブにキャプチャして記録するようにアプリケーションを準備しないことを指定する場合は `false` に設定します。  
  
## <a name="remarks"></a>コメント  
 コンス トラクターが呼び出されたとき`bDefaultInit`に設定`true`、方法によって、グラフィックス ログ ファイルのファイル名を特定`DONT_SAVE_VSGLOG_TO_TEMP`と`VSG_DEFAULT_RUN_FILENAME`する前にプリプロセッサ シンボルが定義されている`vsgcapture.h`アプリに含まれます。  
  
 `bDefaultInit` が `false` に設定された状態でコンストラクターが呼び出された場合、後で `Init` 関数を呼び出して、グラフィックス情報をアクティブにキャプチャして記録するようにグラフィック診断のアプリ内コンポーネントを準備できます。  
  
## <a name="see-also"></a>関連項目  
 [VsgDbg:: ~ VsgDbg (デストラクター)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
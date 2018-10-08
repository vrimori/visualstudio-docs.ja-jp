---
title: '方法: エディット コンティニュを有効にして無効化 |Microsoft Docs'
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57a9ec8b8e25da6edb36e1983e45f7bb78251208
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536914"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>方法 : エディット コンティニュを有効および無効にする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 有効にして編集を無効にして続行](https://docs.microsoft.com/visualstudio/debugger/how-to-enable-and-disable-edit-and-continue)します。  
  
無効にするかでエディット コンティニュを有効にすることができます、**オプション**デザイン時にダイアログ ボックス。 デバッグの最中にこの設定を変更することはできません。  
  
 エディット コンティニュはデバッグ ビルドでのみ動作します。 ネイティブ C++ については、エディット コンティニュで /INCREMENTAL オプションを使用する必要があります。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-enabledisable-edit-and-continue"></a>[エディット コンティニュ] を有効または無効にするには  
  
1.  デバッグ オプション ページを開く (**ツール/オプション/デバッグ**)。  
  
2.  下へスクロールして**エディット コンティニュ**カテゴリ。  
  
3.  を有効にするのには、選択、**編集を有効にして続行**チェック ボックスをオンします。 無効にするには、このチェック ボックスをオフにします。  
  
    > [!NOTE]
    >  IntelliTrace が有効になっている場合に、IntelliTrace イベントと呼び出し情報の両方を収集すると、エディット コンティニュが無効になります。 詳細については、次を参照してください。[構成 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)します。  
  
4.  **[OK]** をクリックします。  
  
 これらのオプションの詳細については、次を参照してください。 [General, Debugging, オプション ダイアログ ボックス](../debugger/general-debugging-options-dialog-box.md)します。  
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ](../debugger/edit-and-continue.md)




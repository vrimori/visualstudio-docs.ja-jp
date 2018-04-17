---
title: '方法: を有効にし、編集を無効にし、続行 (c#、VB、C++) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: c63f629bd0ba67156395b7bf1f1e142355ae9981
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>方法: を有効にし、編集を無効にし、続行 (c#、VB、C++)
無効にするかでエディット コンティニュを有効にすることができます、**オプション**デザイン時にダイアログ ボックス。 デバッグの最中にこの設定を変更することはできません。  
  
エディット コンティニュはデバッグ ビルドでのみ動作します。 ネイティブ C++ については、エディット コンティニュで /INCREMENTAL オプションを使用する必要があります。 C++ では機能の要件の詳細については、これを参照して[ブログの投稿](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)と[エディット コンティニュ (Visual C)](../debugger/edit-and-continue-visual-cpp.md)です。
  
#### <a name="to-enabledisable-edit-and-continue"></a>[エディット コンティニュ] を有効または無効にするには  
  
1.  デバッグ セッションの場合は、デバッグの停止 (**shift キーを押しながら f5 キーを押して**)。

2.  デバッグ オプション ページを開く (**ツール > オプション > デバッグ**)。
  
3.  選択**全般**、まで下にスクロール**エディット コンティニュ**カテゴリ (右側のウィンドウ)。  
  
4.  選択、 **エディット コンティニュ**チェック ボックスをオンします。 無効にするには、このチェック ボックスをオフにします。  
  
    > [!NOTE]
    >  IntelliTrace が有効になっている場合に、IntelliTrace イベントと呼び出し情報の両方を収集すると、エディット コンティニュが無効になります。 詳細については、次を参照してください。 [IntelliTrace](../debugger/intellitrace.md)です。

5. (C++)を有効にするには選択**ネイティブ エディット コンティニュ**です。 無効にするには、このチェック ボックスをオフにします。

6. (C++)ネイティブ コードの追加オプションを設定します。

    - **変更を適用で続行 (ネイティブのみ)**  
        Visual Studio は、ブレーク状態からプロセスを続行するとき、未処理のコード変更を自動的にコンパイルして適用します。 選択されていない場合は デバッグ メニューで コードの変更を適用する"アイテムを使用して変更を適用することもできます。  
  
    - **古いコード (ネイティブのみ) に関する警告します。**  
        古いコードに関する警告を取得します。 
  
7.  **[OK]**をクリックします。    
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ](../debugger/edit-and-continue.md)
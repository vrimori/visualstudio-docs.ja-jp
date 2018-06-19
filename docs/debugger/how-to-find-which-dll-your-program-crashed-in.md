---
title: '方法: いる DLL でクラッシュしたプログラムの検索 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 350cd8a78780eb8ddb2a197ed1e8920fda23bbf3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474828"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>方法 : プログラムのクラッシュが発生している DLL を確認する
  
 システム DLL または他の開発者が作成したコードを呼び出す部分でアプリケーションがクラッシュした場合、クラッシュが発生した DLL を確認する必要があります。 独自のプログラムの外部 DLL でクラッシュが発生した場合、場所を使用して、識別できます、**モジュール**ウィンドウです。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>[モジュール] ウィンドウを使ってクラッシュの発生場所を確認するには  
  
1.  クラッシュが発生したアドレスをメモします。

    アドレスが、エラー メッセージに表示されない場合は、別の方法を使用して、DLL を特定する必要があります。 システム DLL を疑いがある場合は[シンボルを読み込む](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)デバッグするときに、Microsoft シンボル サーバーからです。 それ以外の場合、する必要があります[ダンプ ファイルを作成](../debugger/using-dump-files.md)ヒープ情報代わりに使用します。 さまざまな[ツール](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)ダンプ ファイルを作成します。
  
2.  **デバッグ** メニューの 選択**Windows**、 をクリック**モジュール**です。  
  
3.  **モジュール**ウィンドウで、検索、**アドレス**列です。 必要に応じて、スクロール バーを使用します。  
  
4.  クリックして、**アドレス**アドレスによって、Dll を並べ替える列の上部にあるボタンをクリックします。  
  
5.  並べ替えたリストを検索して、アドレス範囲内にクラッシュ場所がある DLL を探します。  
  
6.  見て、**名前**と**パス**DLL の名前とパスを表示する列。  
  
## <a name="see-also"></a>関連項目  
 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)   
 [方法 : [モジュール] ウィンドウを使用する](../debugger/how-to-use-the-modules-window.md)
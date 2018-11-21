---
title: '方法: プログラム クラッシュが発生している DLL 確認 |Microsoft Docs'
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
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257098"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>方法: プログラムでクラッシュしている DLL を検索 (C#、C++、Visual Basic、 F#)
  
 システム DLL または他の開発者が作成したコードを呼び出す部分でアプリケーションがクラッシュした場合、クラッシュが発生した DLL を確認する必要があります。 プログラム外の DLL でクラッシュが発生した場合を使用して場所を識別できます、**モジュール**ウィンドウ。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>[モジュール] ウィンドウを使ってクラッシュの発生場所を確認するには  
  
1.  クラッシュが発生したアドレスをメモします。

    アドレスが、エラー メッセージに表示されない場合は、別の方法を使用して DLL を特定する必要があります。 システム DLL を疑いがある場合は、[シンボルを読み込む](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)デバッグするときに、Microsoft シンボル サーバーからです。 それ以外の場合、する必要があります[ダンプ ファイル作成](../debugger/using-dump-files.md)で情報を代わりにヒープします。 さまざまな[ツール](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)ダンプ ファイルを作成します。
  
2.  **デバッグ** メニューの 選択**Windows**、 をクリック**モジュール**します。  
  
3.  **モジュール**ウィンドウで、検索、**アドレス**列。 必要に応じて、スクロール バーを使用します。  
  
4.  をクリックして、**アドレス**アドレスによって、Dll を並べ替える列の上部にあるボタンをクリックします。  
  
5.  並べ替えたリストを検索して、アドレス範囲内にクラッシュ場所がある DLL を探します。  
  
6.  見て、**名前**と**パス**DLL の名前とパスを表示する列。  
  
## <a name="see-also"></a>関連項目  
 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)   
 [方法 : [モジュール] ウィンドウを使用する](../debugger/how-to-use-the-modules-window.md)
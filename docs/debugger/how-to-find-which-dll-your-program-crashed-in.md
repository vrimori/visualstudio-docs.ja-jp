---
title: '方法: プログラム クラッシュが発生している DLL 確認 |Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9414a91c49b152149cfe13f511ec27e2f4ea9f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965342"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>方法: プログラムでクラッシュしている DLL を検索 (C#、C++、Visual Basic、 F#)
  
 システム DLL または他の開発者が作成したコードを呼び出す部分でアプリケーションがクラッシュした場合、クラッシュが発生した DLL を確認する必要があります。 プログラム外の DLL でクラッシュが発生している場合は、**[モジュール]** ウィンドウを使用してその場所を確認できます。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>[モジュール] ウィンドウを使ってクラッシュの発生場所を確認するには  
  
1.  クラッシュが発生したアドレスをメモします。

    アドレスが、エラー メッセージに表示されない場合は、別の方法を使用して DLL を特定する必要があります。 システム DLL を疑いがある場合は、[シンボルを読み込む](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)デバッグするときに、Microsoft シンボル サーバーからです。 それ以外の場合、する必要があります[ダンプ ファイル作成](../debugger/using-dump-files.md)で情報を代わりにヒープします。 さまざまな[ツール](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)ダンプ ファイルを作成します。
  
2.  **[デバッグ]** メニューの **[ウィンドウ]** をポイントし、**[モジュール]** をクリックします。  
  
3.  **[モジュール]** ウィンドウの **[アドレス]** 列に注目します。 必要に応じて、スクロール バーを使用します。  
  
4.  列の上部にある **[アドレス]** ボタンをクリックして、DLL をアドレス順に並べ替えます。  
  
5.  並べ替えたリストを検索して、アドレス範囲内にクラッシュ場所がある DLL を探します。  
  
6.  **[名前]** 列と **[パス]** 列で、DLL の名前とパスを確認します。  
  
## <a name="see-also"></a>関連項目
 [DLL プロジェクトをデバッグする](../debugger/debugging-dll-projects.md)   
 [方法: [モジュール] ウィンドウを使用する](../debugger/how-to-use-the-modules-window.md)

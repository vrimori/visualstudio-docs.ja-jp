---
title: "エディット コンティニュのエラー メッセージ ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01cd34aacb4abea5f2f3ce29fcb53ba34aaeaf21
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="edit-and-continue-error-message-dialog-box"></a>エディット コンティニュ エラー メッセージ ダイアログ ボックス
エディット コンティニュをサポートする言語でデバッグしているときに、このダイアログ ボックスが表示されますが、**エディット コンティニュ**は行ったコード変更の種類を使用できません。 ダイアログ ボックス内のエラー メッセージに、より詳しい説明が示されます。 このダイアログ ボックスが表示される原因としては、次のことが考えられます。  

-   SQL Server コードを編集しようとした。

-   最適化されたコードを編集しようとした。 (デバッグ ビルドでは、リリース ビルドから切り替える必要があります)。

-   実行中にコードを編集しようとしました。 (の代わりに、デバッガーで一時停止中に)。 再試行[ブレークポイントを設定する](../debugger/using-breakpoints.md)および一時停止中にコードを編集します。

-   アンマネージ デバッグを有効にしているときに、マネージ コードを編集しようとした。 エディット コンティニュでは機能しません[混合モード デバッグ](../debugger/how-to-debug-in-mixed-mode.md)です。

-   行ったコードの変更、プログラミング言語で、エディット コンティニュでサポートされていません。 詳細については、サポートされていないコードの変更についてのトピックを参照してください。 [c#](../debugger/supported-code-changes-csharp.md)、 [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)、および[C++](../debugger/supported-code-changes-cpp.md)です。
  
-   関連付けられているからではなく、プログラムでコードを編集しようとした、**デバッグ**メニュー。  
  
-   ワトソン博士のダンプをデバッグしているときに、デバッグ  
  
-   未処理の例外が発生した後のコードとオプションを編集しようとしました。"**未処理の例外で呼び出し履歴をアンワインド**"が選択されていません。  
  
-   埋め込まれたランタイム アプリケーションをデバッグしているときに、コードを編集しようとした。
  
-   4.5.1、前に .NET Framework のバージョンを使用してマネージ コードを編集しようとして、対象が 64 ビット アプリケーションです。 エディット コンティニュを使用する場合は、デバッグ対象を x86 に設定する必要があります  (*projectname* **プロパティ**、**コンパイル** タブで、**コンパイラの高度な**設定します。)。  
  
-   デバッグ中に変更され、再読み込みされたアセンブリのコードを編集しようとした。  
  
-   読み込まれていないアセンブリのコードを編集しようとした。  
  
-   新しいバージョンでビルド エラーが発生したため、古いバージョンでアプリケーションのデバッグを開始した。
  
## <a name="uielement-list"></a>UIElement の一覧  
 **わかりました**  
 ダイアログ ボックスを閉じ、直前の編集操作をキャンセルします。  
  
## <a name="see-also"></a>参照  
 [C++ の編集と続行ブログを投稿します。](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [サポートされているコード変更 (C++)](../debugger/supported-code-changes-cpp.md)
---
title: "エディット コンティニュ (Visual C) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7099fdc72bc93d86d49727eb782d2fd072ec1e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="edit-and-continue-visual-c"></a>エディット コンティニュ (Visual C++)
Visual C++ プロジェクトでエディット コンティニュを使用できます。 参照してください[サポート コードの変更 (C++)](../debugger/supported-code-changes-cpp.md)制限については、エディット コンティニュのです。
  
Visual Studio 2015 Update 3 の機能強化の詳細については、次を参照してください。 [Visual Studio 2015 Update 3 で C++ のエディット コンティニュ](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)です。  
  
 [(強化に最適化されたデータのデバッグ)/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) Visual Studio 2013 Update 3 で導入されたコンパイラ オプションではなくコンパイルされたバイナリのシンボル (.pdb) ファイルに追加情報を追加、 [/Od (無効 (デバッグ))](http://msdn.microsoft.com/library/aafb762y.aspx)オプション。  
  
 **/Zo**エディット コンティニュを無効にします。 参照してください[する方法: 最適化されたコードをデバッグ](../debugger/how-to-debug-optimized-code.md)です。  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> エディット コンティニュを有効または無効にする  
 現在のデバッグ セッション中に適用しないコードの編集を行う場合は、エディット コンティニュの自動起動を無効にすることもできます。 自動エディット コンティニュをもう一度有効にすることもできます。

> [!IMPORTANT]
> 必要なビルド設定やその他の機能の互換性についてを参照してください [C++ のエディット コンティニュ Visual Studio 2015 Update 3] (https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/ です。
  
1.  デバッグ セッションの場合は、デバッグの停止 (**shift キーを押しながら f5 キーを押して**)。

2. **[ツール]** メニューの **[オプション]**をクリックします。
  
3.  **オプション**ダイアログ ボックスで、**デバッグ > 全般**です。

4.  を有効にするには選択**エディット コンティニュ**です。 無効にするには、チェック ボックスをオフにします。
  
5.  **[エディット コンティニュ]** グループで、 **[ネイティブのエディット コンティニュを有効にする]** チェック ボックスをオンまたはオフにします。  
  
 この設定を変更すると、作業するすべてのプロジェクトに影響します。 この設定の変更後にアプリケーションをリビルドする必要はありません。 アプリケーションをコマンドラインまたはメイクファイルでビルドする場合は、Visual Studio 環境でデバッグすることができますも使用するエディット コンティニュを設定した場合、 **/ZI**オプション。  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> コード変更を明示的に適用する方法  
 Visual C++ では、エディット コンティニュは 2 つの方法でコード変更を適用できます。 実行コマンドを選択した場合、コード変更は暗黙的に適用できます。 **[コード変更を適用]** を使用した場合は明示的に適用できます。  
  
 コードの変更を明示的に適用するときに、プログラムに残ります中断モードの実行は行われません。  
  
-   コードの変更を明示的に適用するには、**[デバッグ]** メニューで **[コード変更を適用]** を選択します。  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> コード変更を停止する方法  
 エディット コンティニュがコード変更を適用するプロセスを実行している間、その操作は中断できます。  
  
 コードの変更内容の適用を停止するには  
  
-   **[デバッグ]** メニューの **[コード変更の適用を停止]**をクリックします。  
  
 このメニュー項目は、コード変更の適用中にのみ表示されます。  
  
 このオプションを選択すると、コードの変更内容は一切コミットされません。  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> 実行ポイントをリセットする方法  
 コードを変更してエディット コンティニュでその変更内容を適用すると、実行ポイントが新しい位置に移動する場合があります。 [エディット コンティニュ] では、実行ポイントができるだけ正確に位置付けられますが、結果が常に正しいとは限りません。  
  
 Visual C++ では、実行ポイントが変わると、それを示すダイアログ ボックスが表示されます。 デバッグを継続する前に、位置が正しいかどうかを確認する必要があります。 位置が正しくない場合は、 **[次のステートメントの設定]** を使用します。 詳しくは、「 [次に実行されるステートメントを設定する](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute)」をご覧ください。  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> 古いコードを操作する方法  
 場合により、エディット コンティニュがコード変更を直ちに適用して実行可能にできないことがありますが、デバッグを続行すると、後でコード変更が適用できるようになる場合もあります。 これは、現在の関数を呼び出す関数を編集した場合や、呼び出し履歴上の関数に 64 バイトを超える新しい変数を追加した場合に発生します。  
  
 このような場合、変更が適用されるまで、デバッガーは元のコードを続けて実行します。 古いコードは、一時的なソース ファイル ウィンドウとして、 `enc25.tmp`などのタイトルで別のソース ウィンドウに表示されます。 編集されたソース コードは、元のソース ウィンドウに表示されます。 古いコードを編集しようとすると、警告メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [サポートされているコード変更 (C++)](../debugger/supported-code-changes-cpp.md)
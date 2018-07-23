---
title: ソース管理プラグインを実装するためのベスト プラクティス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16699f520390c0bc4f062f9db82e66a26ef5fd8f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154210"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装するためのベスト プラクティス
次の技術的な詳細を使用して、ソース管理のプラグインを確実に実装できる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="memory-management-issues"></a>メモリ管理に関する問題  
 ほとんどの場合、呼び出し元である、統合開発環境 (IDE) は解放し、メモリの割り当てとします。 ソース管理プラグインは、呼び出し元が割り当てたバッファー内の文字列とその他の項目を返します。 例外が発生した特定の関数の説明に記載されています。  
  
## <a name="arrays-of-file-names"></a>ファイル名の配列  
 ファイルの配列が渡されるときに、連続したファイル名の配列としては渡されません。 ファイル名へのポインターの配列として渡されます。 など、 [SccGet](../extensibility/sccget-function.md)、によってファイル名が渡される、`lpFileNames`パラメーター、場所`lpFileNames`へのポインターでは実際には、`char **`します。 `lpFileNames`[0]、名へのポインターは、 `lpFileNames`[1] と 2 つ目の名前へのポインターです。  
  
## <a name="large-model"></a>大規模なモデル  
 すべてのポインターは、32 ビット、16 ビットのオペレーティング システム上であってもです。  
  
## <a name="fully-qualified-paths"></a>完全修飾パス  
 場所のファイル名またはディレクトリが引数として指定されて、完全修飾パスまたは UNC パス、最後の円記号なし必要があります。 これらを基になるソース管理システムの要件である場合、相対パスに変換するプラグインのソース管理の役目です。  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>登録済みの DLL の完全修飾パスを指定します。  
 IDE は不要になった、相対パスから Dll を読み込みます (たとえば、 *.\NewProvider.dll*)。 DLL の完全なパスを指定する必要があります (たとえば、 *C:\Providers\NewProvider.dll*)。 この要件は、承認されていないか、権限を借用したソース管理 Dll の読み込みを防止することで、IDE のセキュリティを強化します。  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>ソース管理プラグインをインストールするときに、既存の VSSCI プラグインの確認します。  
 ソース管理プラグインをインストールすることを計画しているユーザーは、既存のソース管理プラグインのコンピューターにインストールを用意しています。 インストール (セットアップ) プログラム プラグインの作成する必要がありますを決定、関連するレジストリ キーの既存の値があるかどうか。 これらのキーは既に設定されている場合、インストール プログラムは、ユーザーに求めます既定のソース管理プラグインとプラグインの登録し、既にインストールされている 1 つを置換するかどうか。  
  
## <a name="error-result-codes-and-reporting"></a>エラー結果コードとレポート  
 `SCC_OK`返す制御関数のソース コードでは、すべてのファイルの操作が成功したことを示します。 操作に失敗した場合を最後に発生したエラー コードを返すことが必要です。  
  
 レポートのルールでは、IDE でエラーが発生した場合、IDE がレポートする責任を負います。 ソース管理システムでエラーが発生する場合、ソース管理プラグインでは、同じ結果がレポートする責任を負います。 たとえば、**ファイルが現在選択されていない**は IDE によって報告される**このファイルは既にチェック アウト**プラグインによって報告されます。  
  
## <a name="the-context-structure"></a>Context 構造体  
 呼び出し中に、 [SccInitialize](../extensibility/sccinitialize-function.md)、呼び出し元のパス、`ppvContext`パラメーター、void を初期化されていないハンドル。 ソース管理プラグインは、このパラメーターを無視できますか、任意の種類の構造体を割り当て、渡されたポインターにすることで、ポインターを置きます。 IDE では、この構造体を理解しませんが、プラグインで他のすべての呼び出しにこの構造体へのポインターを渡します。 グローバル変数を使用せず、関数呼び出し間で保持されるグローバル状態情報を維持するために使用できること、プラグインに貴重なコンテキスト キャッシュ情報を提供します。 プラグインがへの呼び出しで構造体を解放する、 [SccUninitialize](../extensibility/sccuninitialize-function.md)します。  
  
 場合プラグインのセット、`SCC_CAP_REENTRANT`ビット、 [SccInitialize](../extensibility/sccinitialize-function.md) (具体的には、`lpSccCaps`パラメーター)、複数のコンテキストの構造が開いているすべてのプロジェクトを追跡するために使用されます。  
  
## <a name="bitflags-and-other-command-options"></a>ビットフラグとその他のコマンド オプション  
 コマンドごとなど、 [SccGet](../extensibility/sccget-function.md)IDE は、コマンドの動作を変更する多くのオプションを指定できます。  
  
 API を介して、IDE によって特定のオプションの設定をサポートする、`fOptions`パラメーター。 これらのオプションの説明を[特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)と共にそれらに影響を与えるコマンド。 一般に、これらは、対象のユーザーが求められないオプションです。  
  
 ソース管理プラグインの間で大きく異なるため、最もユーザー構成可能なオプションの設定では、この方法で定義されていません。そのため、推奨されるメカニズムは、 **[詳細設定]** ボタンをクリックします。 などの**取得**ダイアログ ボックスで、IDE を表示情報だけを認識するが、表示することも、 **[詳細設定]** プラグインがこのコマンドのオプション ボタンをクリックします。 ユーザーがクリックすると、**詳細**ボタン、IDE の呼び出し、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)ビットフラグまたは日付/時刻などの情報をユーザーに確認するプラグインのソース管理を有効にします。 プラグインに戻る際に渡される構造体でこの情報を返します、`SccGet`コマンド。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインを作成します。](../extensibility/internals/creating-a-source-control-plug-in.md)
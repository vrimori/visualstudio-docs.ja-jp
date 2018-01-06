---
title: "ソース管理プラグインを実装するためのベスト プラクティス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e406bc0cd5d7e4cb082e1f5e34fa6645538d02ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>ソース管理プラグインを実装するためのベスト プラクティス
次の技術的な詳細を使用して、ソース管理のプラグインを確実に実装できる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="memory-management-issues"></a>メモリ管理に関する問題  
 ほとんどの場合、呼び出し元である、統合開発環境 (IDE) は解放し、メモリを割り当てます。 ソース管理プラグインは、呼び出し元が割り当てたバッファー内の文字列とその他の項目を返します。 例外が発生した特定の機能の説明に記載されています。  
  
## <a name="arrays-of-file-names"></a>ファイル名の配列  
 ファイルの配列が渡されるときに、連続したファイル名の配列として渡されるされません。 ファイル名へのポインターの配列として渡されます。 たとえば、 [SccGet](../extensibility/sccget-function.md)、によってファイル名が渡される、`lpFileNames`パラメーター、場所`lpFileNames`へのポインターでは実際には、`char **`です。 `lpFileNames`[0]、名へのポインターは、 `lpFileNames`[1] と 2 番目の名前へのポインターです。  
  
## <a name="large-model"></a>大規模なモデル  
 すべてのポインターは、16 ビットのオペレーティング システム上でも、32 ビットです。  
  
## <a name="fully-qualified-paths"></a>完全修飾パス  
 ここで、ファイル名、またはディレクトリが引数として指定されている必要がある完全修飾パスまたは UNC パス、最後の円記号なし。 ソース管理プラグインに変換する場合は、基になるソース管理システムの要件は、相対パスにこれらの役割です。  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>登録済みの DLL の完全修飾パスを指定します。  
 IDE では、相対パス (たとえば、.\NewProvider.dll) からに Dll が読み込まれない。 (たとえば、C:\Providers\NewProvider.dll) DLL の完全なパスを指定する必要があります。 この要件は、承認されていないか、権限を借用したソース管理 Dll の読み込みを実行できないようにして、IDE のセキュリティを強化します。  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>ソース管理プラグインをインストールするときに、既存の VSSCI プラグインの確認します。  
 ソース管理プラグインをインストールすることを計画したユーザーが、既存のソース管理プラグイン コンピューターにインストールされている既にあります。 インストール (セットアップ) プログラム プラグインを作成する必要がありますを確認に関連するレジストリ キーの既存の値があるかどうか。 これらのキーは既に設定されている場合、インストール プログラム必要がありますを求め、既定のソース管理プラグインとプラグインの登録し、既にインストールされている 1 つを置換するかどうか。  
  
## <a name="error-result-codes-and-reporting"></a>エラー結果コードとレポート  
 `SCC_OK`返すソース制御関数のコードでは、すべてのファイルの操作が成功したことを示します。 操作が失敗した場合を最後に発生したエラー コードを返すことが必要です。  
  
 レポート作成用の規則は、IDE では、エラーが発生する場合、IDE ことの報告の責任です。 ソース管理システムでエラーが発生する場合、ソース管理プラグインは報告をします。 たとえば、「ファイルが現在選択されていません」が報告されます、IDE で"このファイルは既にチェック アウト"が、プラグインで報告される一方。  
  
## <a name="the-context-structure"></a>Context 構造体  
 呼び出し中に、 [SccInitialize](../extensibility/sccinitialize-function.md)、呼び出し元のパス、`ppvContext`パラメーターは、void を初期化されていないハンドルです。 ソース管理プラグインは、このパラメーターを無視してかまいませんまたは任意の種類の構造体を割り当て、その構造に渡されたポインターにポインターを格納します。 IDE は、この構造を認識しませんが、プラグインの他のすべての呼び出しにこの構造体へのポインターを渡します。 グローバル変数を使用せずに関数呼び出しで保持されるグローバル状態情報を維持するために使用できることをプラグインする貴重なコンテキスト キャッシュについて情報を提供します。 プラグインへの呼び出しで構造体を解放する、 [SccUninitialize](../extensibility/sccuninitialize-function.md)です。  
  
 場合、プラグインのセット、`SCC_CAP_REENTRANT`内のビット、 [SccInitialize](../extensibility/sccinitialize-function.md) (具体的には、`lpSccCaps`パラメーター)、複数のコンテキスト構造が開いているすべてのプロジェクトを追跡するために使用されます。  
  
## <a name="bitflags-and-other-command-options"></a>ビットフラグおよびその他のコマンド オプション  
 各コマンドのように、 [SccGet](../extensibility/sccget-function.md)IDE は、コマンドの動作を変更できる多くのオプションを指定できます。  
  
 API を介して、IDE によって特定のオプションの設定を使用して、`fOptions`パラメーター。 これらのオプションの説明を[ビットフラグが特定のコマンドで使用される](../extensibility/bitflags-used-by-specific-commands.md)と共にに影響を与えるコマンド。 一般に、これらがオプションをユーザーがない入力が求められます。  
  
 最もユーザー構成可能なオプションの設定は、ソース管理プラグインの間で大きく異なるため、この方法で定義されていません。そのため、推奨される機構、**詳細**ボタンをクリックします。 インスタンスで、**取得**ダイアログ ボックスで、IDE を表示情報のみを認識するが、表示することも、 **[詳細設定]**プラグインがこのコマンドのオプション ボタンをクリックします。 ユーザーがクリックしたとき、 **[詳細設定]**  ボタン、IDE の呼び出し、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)ビットフラグまたは日付/時刻などの情報をユーザーに確認するプラグインのソース管理を有効にします。 プラグインに戻る時に渡される構造体でこの情報を返します、`SccGet`コマンド。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)
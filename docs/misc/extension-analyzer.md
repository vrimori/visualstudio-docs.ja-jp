---
title: "拡張機能アナライザー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage、読み込みエラー アナライザー"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 拡張機能アナライザー
**拡張子機能アナライザー**は、最も一般的な拡張機能の読み込みエラーをキャプチャしてログに記録します。**拡張機能アナライザー**は、独自のツール ウィンドウで実行されます。 アナライザーは、エラーの原因とその修正方法に関する推奨事項を報告します。  
  
 [拡張機能アナライザー](http://go.microsoft.com/fwlink/?LinkId=205840)は、Visual Studio ギャラリーからダウンロードできます。**拡張機能アナライザー** アセンブリは、\<*Visual Studio installation path*\>\\Common7\\IDE\\PrivateAssemblies\\ にインストールされます。  
  
## ブラウザー  
 **拡張機能アナライザー**をインストールしたら、**\[ツール\]** メニューで、**\[拡張機能アナライザー\]**、**\[ブラウザー\]** の順にクリックします。 ウィンドウが表示され、コンピューターに登録されているすべての拡張機能が一覧表示されます。 VSIX files、VSPackages、PkgDef ファイル、MEF といったコンポーネントごとにタブがあります。 任意の列名で一覧を並べ替えることができます。  
  
1.  VSIX タブには、インストール済みの VSIX 拡張機能に関する情報が表示されます。**\[Show System Components\]** \(システム コンポーネントを表示\) チェックボックスをオンにすることでシステム コンポーネントを含めることができます。 このタブで、VSIX のログ エントリに移動し、Visual Studio XML エディターで VSIX マニフェストを開き、VSIX 拡張機能がインストールされているフォルダーを開くことができます。  
  
2.  \[VS Packages\] \(VS パッケージ\) タブには、読み込まれているかどうかに関係なく、現在 Visual Studio に認識されている VSPackages に関する情報が表示されます。 この情報には、VSIX 識別子、.pkgdef ファイル、および VSPackage の GUID が含まれます。**\[Show System Packages\]** \(システム パッケージを表示\) チェックボックスをオンにすることでシステムの VSPackages を含めることができます。 このタブで、ログ エントリへの移動、\[VSIX\] タブでの VSIX の一覧表示、\[PkgDef Files\] \(PkgDef ファイル\) タブでの .pkgdef ファイルの表示、および VSPackage の分析を行うことができます。 分析の結果は、**\[出力\]** ウィンドウに表示されます。  
  
3.  \[PkgDef Files\] \(PkgDef ファイル\) タブには、Visual Studio で認識されている .pkgdef ファイルに関する情報が表示されます。 この情報には、VSIX の識別子、および拡張機能のパスが含まれます。 ログまたは \[VSIX\] タブに移動し、エディターで .pkgdef ファイルを表示できます。  
  
4.  \[MEF Components\] \(MEF コンポーネント\) タブには、Visual Studio に認識されている MEF コンポーネントに関する情報が表示されます。 この情報には、VSIX の識別子、および拡張機能のインストール先のパスが含まれます。**\[Show System Components\]** \(システム コンポーネントを表示\) チェックボックスをオンにすることでシステム コンポーネントを含めることができます。 対応する VSIX エントリ、.pkgdef ファイル、および拡張機能のインストール場所に移動することもできます。  
  
> [!WARNING]
>  Fusion ログを有効にするように求めるメッセージが表示されることがあります。 これを行うには、ログ ファイルの場所を選択します。 続行する前に Visual Studio のすべてのインスタンスの再起動を求めるメッセージが表示されることがあります  
  
## ログ ビューアー  
 ログ機能が有効になっている \(プロジェクトのコマンドライン引数に \/log を追加します\) プロジェクトを実行している場合は、**\[Extension Log Viewer\]** \(拡張機能ログ ビューアー\) でログ メッセージを表示できます。 詳細については、「[\/Log](../ide/reference/log-devenv-exe.md)」を参照してください。**\[Extension Log Viewer\]** \(拡張機能ログ ビューアー\) ウィンドウには、日付、リスナー、エントリの種類 \(メッセージの種類\)、エラーの種類、クラス\/インターフェイス情報、ログ メッセージが表示されます。 情報を並べ替えてフィルター処理することができます。  
  
## 拡張機能の読み込みに関する一般的な問題  
 次に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での拡張機能の読み込みエラーのいくつかの一般的な原因を示します。  
  
-   依存関係の問題。 依存するアセンブリが見つからないような方法で拡張機能が配置されています。  
  
-   例外。 VSPackage が読み込まれるときに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] が <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> メソッドを呼び出します。 このメソッドが例外をスローした場合、VSPackage の読み込みが失敗します。 この問題を特定する最善の方法は、SetSite コードを調べることです。  
  
-   不適切な登録。 拡張機能が適切に署名されていることおよび VSPackage が正しい公開キーを使用して登録されていることを確認します。  
  
## 参照  
 [Vspackage を管理します。](../extensibility/managing-vspackages.md)
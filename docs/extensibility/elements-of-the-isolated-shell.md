---
title: "分離シェルの要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell、分離モード"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 分離シェルの要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

レジストリ設定、実行時の設定、および、分離シェル アプリケーションとその .vsct、.pkgdef、and.pkgundef ファイルのアプリケーションのエントリ ポイントを変更することができます。  
  
## レジストリ設定  
 .Pkgdef と .pkgundef ファイルの両方は、分離シェル アプリケーションのレジストリ設定を変更します。 このアプリケーションを実行すると、次の順序では、レジストリ設定が定義されています。  
  
 このアプリケーションを実行すると、次の順序では、レジストリ設定が定義されています。  
  
1.  アプリケーションのレジストリ キーが作成されます。  
  
2.  指定したキーとエントリを定義することで、アプリケーションの .pkgdef ファイルから、レジストリを更新しても。  
  
3.  アプリケーションの一部であるすべてのパッケージがパッケージの .pkgdef ファイルから、レジストリを更新します。 各パッケージは $RootKey$ \\Packages\\ によって、アプリケーションの .pkgdef ファイルで定義されている {*vsPackageGuid*} パッケージのキー。  
  
4.  AppEnvConfig.pkgdef および BaseConfig.pkgdef 内から、レジストリを更新して、 *Visual Studio SDK インストール パス*\\Common7\\IDE\\ShellExtensions\\Platform ディレクトリ。 これらのファイルは、Visual Studio の一部も Visual Studio Shell \(分離モード\) 再頒布可能パッケージの一部です。  
  
5.  指定したキーとエントリを削除することで、アプリケーションの .pkgundef ファイルから、レジストリを更新しても。  
  
## 実行時の設定  
 ユーザーは、分離シェル アプリケーションを起動するときに、Visual Studio シェルの開始のエントリ ポイントを呼び出します。 アプリケーションの設定は、アプリケーションの起動時に、次のように定義されます。  
  
1.  Visual Studio シェルでは、特定のキーのアプリケーションのレジストリを確認します。 キーの設定が開始エントリ ポイントへの呼び出しで指定されている場合、その値は、レジストリの値を上書きします。  
  
2.  レジストリにも、エントリ ポイントと、パラメーター、設定の値を指定し、設定の既定値を使用します。  
  
 ユーザーは、コマンドラインから、アプリケーションを起動するときに、すべてのコマンド ライン スイッチは、Devenv では同じ方法ではこれらを扱い、Visual Studio シェルに渡されます。 Devenv のスイッチの詳細については、次を参照してください。 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md) と [VSPackage 開発の Devenv コマンド ライン スイッチ](../extensibility/devenv-command-line-switches-for-vspackage-development.md)です。 コマンド ライン スイッチのパッケージを登録する方法の詳細については、次を参照してください。 [コマンド ライン スイッチを追加します。](../extensibility/adding-command-line-switches.md)します。  
  
## 開始のエントリ ポイント  
 Appenvstub.dll ファイルには、分離シェルにアクセスするためのエントリ ポイントが含まれています。 アプリケーションの起動時に Appenvstub.dll の開始のエントリ ポイントを呼び出します。  
  
 アプリケーションの動作を変更するには、開始のエントリ ポイントに渡される最後のパラメーターの値を変更します。 詳細については、「[分離シェル エントリ ポイントのパラメーター \(C\+\+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md)」を参照してください。  
  
## します。Vsct ファイル  
 .Vsct ファイルを使用して、どの標準の Visual Studio の UI 要素は、アプリケーションで使用を指定できます。 詳細については、「[.Vsct ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)」を参照してください。  
  
## します。Pkgundef ファイル  
 アプリケーションが Visual Studio が既にインストールされているコンピューターにインストールされている場合は、アプリケーションの Visual Studio のレジストリ エントリのコピーが作成されます。 既定は、アプリケーションは、コンピューターに既にインストールされている Vspackage を使用します。 .Pkgundef ファイルでは、アプリケーションから、Visual Studio シェル拡張機能の特定の要素を削除するためにレジストリ エントリを除外できます。 詳細については、「[.Pkgundef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)」を参照してください。  
  
 .Pkgundef ファイルでは、アプリケーションから、Visual Studio シェル拡張機能の特定の要素を削除するためにレジストリ エントリを除外できます。 詳細については、「[.Pkgundef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)」を参照してください。  
  
 パッケージを除外することが Guid のセットは、「 [Visual Studio の機能のパッケージの Guid](../extensibility/package-guids-of-visual-studio-features.md)します。  
  
## します。Pkgdef ファイル  
 .Pkgdef ファイルを使用して、アプリケーションがインストールされている場合に設定されているアプリケーションのレジストリ エントリを定義できます。 .Pkgdef ファイルの説明と、Visual Studio シェルを使用してレジストリ エントリの一覧は、次を参照してください。 [.Pkgdef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)します。  
  
## 代替文字列  
 .Pkgdef および .pkgundef ファイルで使用される代替文字列は、「 [使用される代替文字列。Pkgdef とします。Pkgundef ファイル](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)します。  
  
## その他の設定  
 分離シェル アプリケーションは、Microsoft.VisualStudio.GraphModel.dll に依存する場合は、分離シェル アプリケーションの .config ファイルに次のバインド リダイレクトを追加する必要があります。  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
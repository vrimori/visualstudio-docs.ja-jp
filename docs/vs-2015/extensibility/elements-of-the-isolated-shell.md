---
title: 分離シェルの要素 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9edba9d02b0c02321cd468cdc75630be92d53fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546428"
---
# <a name="elements-of-the-isolated-shell"></a>分離シェルの要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[分離シェルの要素](https://docs.microsoft.com/visualstudio/extensibility/elements-of-the-isolated-shell)します。  
  
レジストリ設定、実行時の設定と、分離シェル アプリケーションとその .vsct、.pkgdef、and.pkgundef ファイルのアプリケーションのエントリ ポイントを変更することができます。  
  
## <a name="registry-settings"></a>レジストリ設定  
 .Pkgdef と .pkgundef ファイルの両方は、分離シェル アプリケーションのレジストリ設定を変更します。 アプリケーションを実行すると、次の順序では、レジストリ設定が定義されています。  
  
 アプリケーションを実行すると、次の順序では、レジストリ設定が定義されています。  
  
1.  アプリケーションのレジストリ キーが作成されます。  
  
2.  レジストリは、指定したキーとエントリを定義することで、アプリケーションの .pkgdef ファイルから更新されます。  
  
3.  アプリケーションの一部であるパッケージごとに、レジストリは、そのパッケージの .pkgdef ファイルから更新されます。 各パッケージは、$RootKey$ \Packages によって、アプリケーションの .pkgdef ファイルで定義されている\\{*vsPackageGuid*} パッケージのキー。  
  
4.  AppEnvConfig.pkgdef とで BaseConfig.pkgdef からレジストリを更新、 *Visual Studio SDK インストール パス*\Common7\IDE\ShellExtensions\Platform ディレクトリ。 これらのファイルは、Visual Studio の一部とも Visual Studio Shell (分離モード) 再頒布可能パッケージの一部です。  
  
5.  レジストリは、指定したキーとエントリを削除することで、アプリケーションの .pkgundef ファイルから更新されます。  
  
## <a name="run-time-settings"></a>実行時の設定  
 ユーザーは、分離シェル アプリケーションを起動するときに、Visual Studio シェルの開始のエントリ ポイントを呼び出します。 アプリケーションの設定は、次のように、アプリケーションの起動時に定義されます。  
  
1.  Visual Studio shell は、特定のキーのアプリケーションのレジストリを確認します。 開始のエントリ ポイントへの呼び出しでキーの設定が指定されている場合、その値は、レジストリの値をオーバーライドします。  
  
2.  レジストリにも、エントリ ポイントと、パラメーターは、設定の値を指定し、設定の既定値を使用します。  
  
 ユーザーは、コマンドラインからアプリケーションを起動するときに、すべてのコマンド ライン スイッチは、Visual Studio shell は、Devenv は同じ方法で扱うに渡されます。 Devenv のスイッチの詳細については、次を参照してください。 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)と[VSPackage 開発の Devenv コマンド ライン スイッチ](../extensibility/devenv-command-line-switches-for-vspackage-development.md)します。 コマンド ライン スイッチ用のパッケージを登録する方法の詳細については、次を参照してください。[コマンド ライン スイッチを追加する](../extensibility/adding-command-line-switches.md)します。  
  
## <a name="the-start-entry-point"></a>開始のエントリ ポイント  
 Appenvstub.dll ファイルには、分離シェルにアクセスするためのエントリ ポイントが含まれています。 アプリケーションの起動時に Appenvstub.dll の開始エントリ ポイントを呼び出します。  
  
 最後の開始のエントリ ポイントに渡されるパラメーターの値を変更することで、アプリケーションの動作を変更できます。 詳細については、次を参照してください。[分離シェル エントリ ポイントのパラメーター (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md)します。  
  
## <a name="the-vsct-file"></a>します。Vsct ファイル  
 .Vsct ファイルでは、標準的な Visual Studio の UI 要素は、アプリケーションで使用可能なを指定できます。 詳細については、次を参照してください。[します。Vsct ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)します。  
  
## <a name="the-pkgundef-file"></a>します。Pkgundef ファイル  
 Visual Studio が既にインストールされているコンピューターで、アプリケーションがインストールされている、Visual Studio のレジストリ エントリのコピーは、アプリケーションのされます。 既定では、アプリケーションは、コンピューターに既にインストールされている Vspackage を使用します。 .Pkgundef ファイルでは、アプリケーションから、Visual Studio シェル拡張機能の特定の要素を削除するためにレジストリ エントリを除外できます。 詳細については、次を参照してください。[します。Pkgundef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)します。  
  
 .Pkgundef ファイルでは、アプリケーションから、Visual Studio シェル拡張機能の特定の要素を削除するためにレジストリ エントリを除外できます。 詳細については、次を参照してください。[します。Pkgundef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)します。  
  
 パッケージを除外することが Guid のセットは、「[パッケージ Guid の Visual Studio 機能](../extensibility/package-guids-of-visual-studio-features.md)します。  
  
## <a name="the-pkgdef-file"></a>します。Pkgdef ファイル  
 .Pkgdef ファイルを使用して、アプリケーションがインストールされている場合に設定されているアプリケーションのレジストリ エントリを定義できます。 .Pkgdef ファイルの説明と、Visual Studio shell を使用するレジストリ エントリの一覧は、次を参照してください。[します。Pkgdef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)します。  
  
## <a name="substitution-strings"></a>代替文字列  
 .Pkgdef と .pkgundef ファイルで使用される代替文字列は、「[で置換文字列を使用します。Pkgdef とします。Pkgundef ファイル](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)します。  
  
## <a name="other-settings"></a>その他の設定  
 分離シェル アプリケーションは、Microsoft.VisualStudio.GraphModel.dll に依存する場合は、分離シェル アプリケーションの .config ファイルに次のバインド リダイレクトを追加する必要があります。  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```


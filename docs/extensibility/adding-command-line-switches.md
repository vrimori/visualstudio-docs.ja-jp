---
title: コマンド ライン スイッチを追加する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ebfc937ee5cf6025761bb9da5d5f6589caf77d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901048"
---
# <a name="add-command-line-switches"></a>コマンド ライン スイッチを追加します。
VSPackage に適用されるコマンド ライン スイッチを追加するときに*devenv.exe*を実行します。 使用<xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>スイッチとそのプロパティの名前を宣言します。 この例では、MySwitch スイッチがという名前の VSPackage のサブクラスの追加**AddCommandSwitchPackage**引数なしで、自動的に読み込まれる VSPackage とします。  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 名前付きパラメーターは、次の説明に表示されます。

||||
|-|-|-|-|
| パラメーター | 説明|
| 引数 | スイッチの引数の数。 "*"、または引数のリスト。 |
| DemandLoad | この設定で 1、それ以外の場合は 0 に設定されている場合は、VSPackage を自動的に読み込みます。 |  
| HelpString | ヘルプ文字列またはリソースの ID 文字列と共に表示する**devenv/でしょうか。** します。 |
| 名前 | スイッチ。 |
| PackageGuid | パッケージの GUID。 |  
  
 引数の最初の値が 0 または 1 では、通常は。 特殊な値を ' *'、コマンドラインの残りの部分全体が、引数であることを示すために使用できます。 これは、ユーザーが、デバッガー コマンド文字列で渡す必要がありますのシナリオのデバッグに役立つことができます。  
  
 DemandLoad 値は`true`(1) または`false`(0)、VSPackage が自動的に読み込まれることを示します。  
  
 HelpString 値が含まれている文字列のリソース ID、 **devenv/でしょうか。** ヘルプを表示します。 この値は、フォーム"#nnn"nnn は整数でなければなりません。 リソース ファイル内の文字列値は、改行文字で終わる必要があります。  
  
 名前値は、スイッチの名前です。  
  
 PackageGuid 値は、このスイッチを実装するパッケージの GUID です。 IDE では、この GUID を使用して、コマンド ライン スイッチを適用するレジストリで、VSPackage を見つけます。  
  
## <a name="retrieve-command-line-switches"></a>コマンド ライン スイッチを取得します。  
 パッケージが読み込まれるときに、次の手順を実行して、コマンド ライン スイッチを取得できます。  
  
1. VSPackage の<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>実装、呼び出し`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>を取得する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>インターフェイス。  
  
2. 呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>をユーザーが入力したコマンド ライン スイッチを取得します。  
  
   次のコードでは、MySwitch コマンド ライン スイッチがユーザーによって入力されたかどうかを確認する方法を示します。  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 パッケージが読み込まれるたびに、コマンド ライン スイッチをチェックするユーザーの責任になります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef ユーティリティ](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
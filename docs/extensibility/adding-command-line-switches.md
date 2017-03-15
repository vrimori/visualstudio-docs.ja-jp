---
title: "コマンド ライン スイッチを追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "追加のコマンド ライン スイッチ"
  - "コマンド ライン スイッチを取得します。"
  - "IVsAppCommandLine::GetOption メソッド"
  - "コマンドライン スイッチ"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# コマンド ライン スイッチを追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Devenv.exe を実行すると、VSPackage に適用されるコマンド ライン スイッチを追加することができます。 使用 <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> スイッチとそのプロパティの名前を宣言します。 この例では、という名前の VSPackage のサブクラスの MySwitch スイッチを追加 **AddCommandSwitchPackage** 引数なしで、自動的に読み込まれる VSPackage にします。  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 名前付きパラメーターが次の表に示すように  
  
 引数  
 スイッチの引数の数。 "\*"、または引数のリスト。  
  
 DemandLoad  
 この設定で 1、それ以外の場合は 0 に設定されている場合は、VSPackage を自動的に読み込みます。  
  
 HelpString  
 ヘルプ文字列またはリソースの ID 文字列を表示する **devenv\/?**します。  
  
 名前  
 スイッチです。  
  
 PackageGuid  
 パッケージの GUID です。  
  
 引数の最初の値は 0 または 1 では通常です。 特殊な値 ' \*' コマンドラインの残りの部分全体が、引数であることを示すために使用できます。 これは、ユーザーがデバッガー コマンド文字列で渡す必要がありますシナリオのデバッグに役立つことができます。  
  
 DemandLoad 値があるか、 `true` \(1\) または `false` \(0\)、VSPackage を自動的に読み込まれることを示します。  
  
 HelpString 値は、devenv に表示される文字列のリソース ID\/でしょうか。ヘルプの表示。 この値は、"\#nnn"nnn には、整数値の形式である必要があります。 リソース ファイル内の文字列値は、改行文字で終了する必要があります。  
  
 名前の値は、スイッチの名前です。  
  
 PackageGuid 値は、このスイッチを実装するパッケージの GUID です。 IDE では、この GUID を使用して、コマンド ライン スイッチを適用するレジストリの VSPackage を見つけます。  
  
## コマンド ライン スイッチを取得します。  
 パッケージが読み込まれるときに、次の手順を完了することで、コマンド ライン スイッチを取得できます。  
  
1.  VSPackage ので <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 実装を呼び出して `QueryService` に <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> を取得する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> インターフェイスです。  
  
2.  呼び出す <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> をユーザーが入力したコマンド ライン スイッチを取得します。  
  
 次のコードは、MySwitch コマンド ライン スイッチをユーザーが入力されているかどうかを確認する方法を示しています。  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 ユーザーの責任において、パッケージが読み込まれるたびに、コマンド ライン スイッチを確認することをお勧めします。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef ユーティリティ](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
---
title: "ファイル名拡張子の動詞を登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動詞を登録します。"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# ファイル名拡張子の動詞を登録します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーションとファイル名拡張子の関連付けは、通常、ユーザーがファイルをダブルクリックしたときに発生する推奨されるアクションを持っています。 これを次に例を開く操作に対応するアクションがリンクされている \(推奨\)。  
  
 HKEY\_CLASSES\_ROOT\\ でにあるシェルのキーを使用して、拡張機能のプログラム id \(ProgID\) に関連付けられている動詞を登録する*progid*\\shell します。 詳細については、次を参照してください。 [ファイルの種類](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)します。  
  
## 標準的な動詞を登録します。  
 オペレーティング システムでは、次の標準的な動詞を認識します。  
  
-   開く  
  
-   編集  
  
-   再生  
  
-   印刷  
  
-   プレビュー  
  
 可能な限り、標準的な動詞を登録します。 最も一般的な選択肢は、Open 動詞です。 ファイルを開くと、ファイルの編集の明確な違いがある場合にのみ、Edit 動詞を使用します。 たとえば、.htm のファイルを開くが表示されますが、ブラウザーが .htm ファイルを編集する HTML エディターを起動します。 標準的な動詞は、オペレーティング システムのロケールでローカライズされます。  
  
> [!NOTE]
>  標準的な動詞を登録するときに、開いているキーの既定値を設定することはしません。 既定値には、メニューの表示文字列が含まれています。 オペレーティング システムには、標準的な動詞にこの文字列が用意されています。  
  
 新しいインスタンスを起動するプロジェクト ファイルを登録する必要があります [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 、ユーザーがファイルを開くとします。 次の例では、標準の動詞の登録、 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] プロジェクトです。  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 既存のインスタンスでファイルを開く [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、DDEEXEC キーを登録します。 次の例では、標準の動詞の登録、 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .cs ファイルです。  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## 既定の動詞の設定  
 既定の動詞は、ユーザーが Windows エクスプ ローラーでファイルをダブルクリックしたときに実行されるアクションです。 既定の動詞は、HKEY\_CLASSES\_ROOT\\ の既定値として指定された動詞*progid*\\Shell キー。 値が指定されていない場合は、最初に、HKEY\_CLASSES\_ROOT\\ に指定された動詞は既定の動詞が*progid*\\Shell キーのリスト。  
  
> [!NOTE]
>  サイド バイ サイド配置で拡張機能の既定の動詞を変更する場合は、インストールと削除の影響を検討してください。 インストール中に元の既定値は上書きされます。  
  
## 参照  
 [Creating a File Association](_win32_file_associations)   
 [サイド バイ サイドのファイルの関連付けを管理します。](../extensibility/managing-side-by-side-file-associations.md)
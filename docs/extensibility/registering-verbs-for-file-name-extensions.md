---
title: ファイル名拡張子の動詞を登録する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a47f45889744db51d68c0f8aeb51b11863823965
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639732"
---
# <a name="register-verbs-for-file-name-extensions"></a>ファイル名拡張子の動詞を登録します。
アプリケーションとファイル名拡張子の関連付けは、通常、ユーザーがファイルをダブルクリックしたときに発生する推奨アクションを持っています。 これは、アクションは、動詞、たとえばオープン操作に対応するにリンクさせます (推奨)。  
  
 シェルのキーを使用して拡張機能があるのプログラム識別子 (ProgID) に関連付けられている動詞を登録する**HKEY_CLASSES_ROOT\{progid} \shell**します。 詳細については、次を参照してください。[ファイルの種類](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)します。  
  
## <a name="register-standard-verbs"></a>標準的な動詞を登録します。  
 オペレーティング システムでは、次の標準的な動詞を認識します。  
  
-   開く  
  
-   編集  
  
-   再生  
  
-   の  
  
-   [プレビュー]  
  
 可能であれば、標準的な動詞を登録します。 最も一般的な選択肢では、Open 動詞です。 ファイルを開くと、ファイルの編集の間の明確な違いがある場合にのみ編集動詞を使用します。 開くなど、 *.htm*ファイルが表示されますが、ブラウザーでの編集は、 *.htm*ファイルは、HTML エディターを起動します。 標準的な動詞は、オペレーティング システムのロケールでローカライズされます。  
  
> [!NOTE]
>  標準的な動詞を登録するときに、開いているキーの既定値を設定しないでください。 既定値には、メニューの表示文字列が含まれています。 オペレーティング システムでは、標準的な動詞にこの文字列を提供します。  
  
 新しいインスタンスを起動するプロジェクト ファイルを登録する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ときに、ユーザーがファイルを開きます。 次の例では、標準の動詞の登録、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]プロジェクト。  
  
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
  
 既存のインスタンスでファイルを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、DDEEXEC キーを登録します。 次の例では、標準の動詞の登録、 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs*ファイル。  
  
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
  
## <a name="set-the-default-verb"></a>既定の動詞を設定します。  
 既定の動詞は、ユーザーが Windows エクスプ ローラーでファイルをダブルクリックしたときに実行されるアクションです。 既定の動詞がの既定値として指定された動詞、 **HKEY_CLASSES_ROOT\\*progid*\Shell**キー。 既定の動詞は、最初の動詞で指定された値が指定されていない場合、 **HKEY_CLASSES_ROOT\\*progid*\Shell**キー リスト。  
  
> [!NOTE]
>  サイド バイ サイドで配置の拡張機能の既定の動詞を変更する場合は、インストールと削除の影響を検討してください。 インストール中に、元の既定値は上書きされます。  
  
## <a name="see-also"></a>関連項目  
 [サイド バイ サイドでのファイルの関連付けを管理します。](../extensibility/managing-side-by-side-file-associations.md)

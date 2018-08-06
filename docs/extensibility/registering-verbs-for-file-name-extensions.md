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
ms.openlocfilehash: 8004176fb64244aecde276226683a53c013d3b31
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513134"
---
# <a name="registering-verbs-for-file-name-extensions"></a>ファイル名拡張子の動詞を登録する
アプリケーションとファイル名拡張子の関連付けは、通常、ユーザーがファイルをダブルクリックしたときに発生する推奨アクションを持っています。 これは、アクションは、動詞、たとえばオープン操作に対応するにリンクさせます (推奨)。  
  
 HKEY_CLASSES_ROOT にあるシェルのキーを使用して、拡張機能のプログラム識別子 (ProgID) に関連付けられている動詞を登録する\\*progid*\shell します。 詳細については、次を参照してください。[ファイルの種類](/windows/desktop/shell/fa-file-types)します。  
  
## <a name="registering-standard-verbs"></a>標準的な動詞を登録します。  
 オペレーティング システムでは、次の標準的な動詞を認識します。  
  
-   開く  
  
-   編集  
  
-   再生  
  
-   の  
  
-   [プレビュー]  
  
 可能であれば、標準的な動詞を登録します。 最も一般的な選択肢では、Open 動詞です。 ファイルを開くと、ファイルの編集の間の明確な違いがある場合にのみ編集動詞を使用します。 たとえば、.htm のファイルを開くに表示されます、ブラウザーは HTML エディターが起動 .htm ファイルを編集します。 標準的な動詞は、オペレーティング システムのロケールでローカライズされます。  
  
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
  
 既存のインスタンスでファイルを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、DDEEXEC キーを登録します。 次の例では、標準の動詞の登録、 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .cs ファイルです。  
  
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
  
## <a name="setting-the-default-verb"></a>既定の動詞の設定  
 既定の動詞は、ユーザーが Windows エクスプ ローラーでファイルをダブルクリックしたときに実行されるアクションです。 既定の動詞は、HKEY_CLASSES_ROOT の既定値として指定された動詞\\*progid*\Shell キー。 値が指定されていない場合、既定の動詞は、HKEY_CLASSES_ROOT に指定された最初の動詞を\\*progid*\Shell キーのリスト。  
  
> [!NOTE]
>  サイド バイ サイドで配置の拡張機能の既定の動詞を変更する場合は、インストールと削除の影響を検討してください。 インストール中に、元の既定値は上書きされます。  
  
## <a name="see-also"></a>関連項目  
 [side-by-side のファイルの関連付けを管理する](../extensibility/managing-side-by-side-file-associations.md)
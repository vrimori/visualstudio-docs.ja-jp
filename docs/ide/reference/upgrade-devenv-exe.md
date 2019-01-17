---
title: -Upgrade (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46e549dfdc661819dac00d0aa965616462130ad0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944724"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
ソリューション ファイルおよびそのすべてのプロジェクト ファイル、または指定されたプロジェクト ファイルを、そのファイルに対応する現在の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の形式に更新します。

## <a name="syntax"></a>構文

```cmd
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>引数
 `SolutionFile`

 ソリューションおよびそのプロジェクト全体をアップグレードする場合は必須です。 ソリューション ファイルのパスと名前です。 ソリューション ファイルの名前のみを入力するか、完全パスと名前を入力できます。 存在しないフォルダー名やファイル名を入力した場合は、フォルダーやファイルが作成されます。

 `ProjectFile`

 単一のプロジェクトをアップグレードする場合、必須です。 ソリューション内のプロジェクト ファイルのパスと名前です。 プロジェクト ファイルの名前のみを入力するか、完全パスと名前を入力できます。 存在しないフォルダー名やファイル名を入力した場合は、フォルダーやファイルが作成されます。

## <a name="remarks"></a>コメント
 バックアップは自動的に作成され、現在のディレクトリに作成される Backup という名前のディレクトリにコピーされます。

 ソース管理されたソリューションまたはプロジェクトは、アップグレードする前にチェックアウトする必要があります。

 `/upgrade` スイッチを使用した場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は起動されません。 アップグレードの結果は、ソリューションまたはプロジェクトの開発言語のアップグレード レポートで参照できます。 エラーや使用方法は返されません。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] でのプロジェクトのアップグレードの詳細については、「[Visual Studio プロジェクトのポート、移行、アップグレード](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)」を参照してください。

## <a name="example"></a>例
 この例では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソリューションの既定フォルダーにある "MyProject.sln" という名前のソリューション ファイルをアップグレードします。

```cmd
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
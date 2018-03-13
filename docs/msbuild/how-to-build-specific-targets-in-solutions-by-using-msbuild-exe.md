---
title: "方法: MSBuild.exe を使用してソリューション内の特定のターゲットをビルドする | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4437c8030f66ae24d94a83d796c0d0edf7e59c79
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>方法 : MSBuild.exe を使用してソリューション内の特定のターゲットをビルドする
MSBuild.exe 使用して、ソリューション内の特定のプロジェクトの特定のターゲットをビルドできます。  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>ソリューション内の特定のプロジェクトの特定のターゲットをビルドするには  
  
1.  コマンド ラインで、`MSBuild.exe <SolutionName>.sln` と入力します。ここで `<SolutionName>` は実行するターゲットを含んでいるソリューションのファイル名に対応します。  
  
2. `/target:` **スイッチの後ろに、`ProjectName`**`:`**`TargetName`** という形式でターゲットを指定します。 文字 `%`、`$`、`@`、`;`、`.`、`(`、`)`、または `'` のいずれかがプロジェクト名に含まれている場合、指定したターゲット名において、それらの文字を `_` に置き換えます。
  
## <a name="example"></a>例  
 次の例では、`NotInSlnFolder` プロジェクトの `Rebuild` ターゲットを実行してから、`NewFolder` ソリューション フォルダーにある `InSolutionFolder` プロジェクトの`Clean` ターゲットを実行します。  
  
```
msbuild SlnFolders.sln /target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean`
```

## <a name="troubleshooting"></a>トラブルシューティング

使用できるオプションを確認したい場合は、MSBuild によって提供されているデバッグ オプションを使用することができます。 環境変数 `MSBUILDEMITSOLUTION=1` を設定し、ソリューションをビルドします。 これにより `<SolutionName>.sln.metaproj` という名前の MSBuild ファイルが作成され、ビルド時に MSBuild によるソリューションの内部ビューが表示されます。 このビューを調べることで、ビルドできるターゲットを特定することができます。

この内部ビューを必要としない場合は、この環境変数を設定した状態でビルドしないでください。 ソリューションでプロジェクトをビルドする際に、この設定が問題を引き起こす可能性があります。

## <a name="see-also"></a>参照  
 [Command-Line Reference (コマンド ライン リファレンス)](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)

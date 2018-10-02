---
title: '[ビルドの詳細設定] ダイアログ ボックス (C#) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a793d20a8d8e0a2773756da32ea252ef200e36c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533485"
---
# <a name="advanced-build-settings-dialog-box-c"></a>[ビルドの詳細設定] ダイアログ ボックス (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[高度なビルドの設定 ダイアログ ボックス (c#)](https://docs.microsoft.com/visualstudio/ide/reference/advanced-build-settings-dialog-box-csharp)します。  
  
  
**プロジェクト デザイナー**の **[ビルドの詳細設定]** ダイアログ ボックスを使用して、プロジェクトの詳細なビルド構成プロパティを指定します。 このダイアログ ボックスは、[!INCLUDE[csprcs](../../includes/csprcs-md.md)] プロジェクトにのみ適用されます。  
  
## <a name="general"></a>全般  
 次のオプションを使用すると、全般的な詳細設定を有効にできます。  
  
 **言語バージョン**  
 使用する言語のバージョンを指定します。 機能セットはバージョンによって異なるので、このオプションを使用して、コンパイラが特定の実装機能のみを許可するように強制したり、既存の標準と互換性のある機能のみを有効にしたりすることができます。 この設定には、次のオプションがあります。  
  
-   **ISO-1**  
  
     ISO-1 の標準機能をターゲットにします。  
  
-   **default**  
  
     現在のバージョンをターゲットにします。  
  
 詳しくは、「[/langversion (C# コンパイラ オプション)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94)」をご覧ください。  
  
 **内部コンパイル エラー報告**  
 コンパイラ エラーを Microsoft に報告するかどうかを指定します。 **prompt** (既定) に設定すると、内部コンパイラ エラーが発生した場合にプロンプトが表示され、エラー報告を電子的に Microsoft に送信するオプションが示されます。 **send** に設定すると、エラー報告は自動的に送信されます。 **queue** に設定すると、報告はキューに追加されます。 **none** に設定すると、エラーはコンパイラのテキスト出力にのみ報告されます。 詳しくは、「[/errorreport (C# コンパイラ オプション)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf)」をご覧ください。  
  
 **演算のオーバーフローおよびアンダーフローのチェック**  
 [checked](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) キーワードまたは [unchecked](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) キーワードのスコープ内に含まれない整数の算術ステートメントと、データ型の範囲外の値になる整数の算術ステートメントで、ランタイム例外が発生するかどうかを指定します。詳細については、「[/checked (C# Compiler Options)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b)」(/checked (C# のコンパイラ オプション)) を参照してください。  
  
 **標準ライブラリ (mscorlib.dll) を参照しない**  
 Mscorlib.dll がプログラム全体を定義にインポートするかどうかを指定します。<xref:System>名前空間。 独自の <xref:System> 名前空間およびオブジェクトを定義または作成する場合は、このチェック ボックスをオンにします。 詳しくは、「[/nostdlib (C# コンパイラ オプション)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f)」をご覧ください。  
  
## <a name="output"></a>出力  
 次のオプションを使用すると、詳細な出力オプションを指定できます。  
  
 **デバッグ情報**  
 コンパイラによって生成されるデバッグ情報の種類を指定します。 アプリケーションのデバッグ パフォーマンスを構成する方法については、「[イメージのデバッグの簡略化](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3)」を参照してください。 この設定には、次のオプションがあります。  
  
-   **none**  
  
     デバッグ情報を生成しないことを指定します。  
  
-   **full**  
  
     実行中のプログラムにデバッガーをアタッチできるようにします。  
  
-   **pdbonly**  
  
     プログラムがデバッガーで開始されたとき、ソース コードのデバッグが有効になりますが、実行中のプログラムがデバッガーにアタッチされているときにのみアセンブラーが表示されます。  
  
 詳しくは、「[/debug (C# コンパイラ オプション)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969)」をご覧ください。  
  
 **ファイルの配置**  
 出力ファイル内のセクションのサイズを指定します。 有効値は **512**、**1024**、**2048**、**4096**、および **8192** です。 これらの値の単位はバイトです。 各セクションは、この値の倍数である境界内にアラインされるので、出力ファイルのサイズに影響があります。 詳しくは、「[/filealign (C# コンパイラ オプション)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073)」をご覧ください。  
  
 **DLL ベース アドレス**  
 DLL を読み込む位置に推奨されるベース アドレスを指定します。 DLL の既定のベース アドレスは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 共通言語ランタイムにより設定されます。 詳しくは、「[/baseaddress (C# コンパイラ オプション)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)   
 [[ビルド] ページ (プロジェクト デザイナー) (C#)](../../ide/reference/build-page-project-designer-csharp.md)




---
title: "Visual Studio でのコンパイルとビルド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 28
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7e372d9d6d935ff40054b8ba3f7684bf5ea9c458
ms.openlocfilehash: aa3d791afc574200157104145617ff6ad6139b68
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="compiling-and-building-in-visual-studio"></a>Visual Studio でのコンパイルとビルド
開発サイクル中、何度も Visual Studio を使用して、アプリケーションをビルドし、アセンブリや実行可能プログラムを作成できます。 コードを何度もビルドすることによって、無効な構文、キーワードのスペルミス、型の不一致などのコンパイル時エラーを早い段階で特定できます。 また、コードのデバッグ バージョンを何度もビルドして実行することにより、ロジック エラーやセマンティック エラーなどの実行時エラーを検出して修正できます。  
  
 プロジェクトまたはソリューションの開発を完了し、十分にデバッグしたら、そのプロジェクトまたはソリューションのコンポーネントをリリース ビルドでコンパイルできます。 既定では、リリース ビルドはデバッグ バージョンよりサイズが小さく実行が高速になるように設計および最適化されます。 詳細については、「[チュートリアル: アプリケーションをビルドする](../ide/walkthrough-building-an-application.md)」を参照してください。  
  
## <a name="choosing-a-build-method"></a>ビルド方法の選択  
 アプリケーションは、IDE の既定のビルド オプション、コマンド プロンプト、または Team Foundation ビルドを使用してビルドできます。 これらの各オプションでは基になるテクノロジとして MSBuild が使用されており、それぞれの方法には次の表に示すような利点があります。  
  
|ビルド方法|利点|詳細情報|  
|------------------|--------------|--------------------------|  
|IDE の使用|-   ビルドをより簡単に作成し、すぐに実行できます。<br />-   C++ および C# のプロジェクトについては、マルチプロセッサ ビルドを実行できます。<br />-   ビルド システムの一部をカスタマイズできます。|[Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|  
|MSBuild コマンド ラインの実行|-   Visual Studio をインストールせずにプロジェクトをビルドできます。<br />-   すべての種類のプロジェクトについて、マルチ プロセッサ ビルドを実行できます。<br />-   ビルド システムのほとんどの部分をカスタマイズできます。|[MSBuild](../msbuild/msbuild.md)|  
|Team Foundation ビルドの使用|-   ビルド プロセスを自動化できます。 たとえば、1 つまたは複数のプロジェクトを夜間にビルドすることも、コードのチェックインごとにビルドすることもできます。 また、開発用コンピューターではなく、共有ビルド サーバーでプロジェクトをビルドできます。<br />-   ビルドするコード、実行するテスト、およびその他のオプションを簡単に指定できます。<br />-   ビルド ワークフローを変更し、必要に応じてビルド アクティビティを作成することで、大幅にカスタマイズされたタスクを実行できます。|[アプリケーションのビルド](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|  
  
## <a name="building-from-the-ide"></a>IDE でのビルド  
 プロジェクトを作成すると、既定のビルド構成が定義され、ビルドのコンテキストを用意するために、既定のソリューション ビルド構成が割り当てられます。 ソリューション構成によって、ソリューション内のプロジェクトをビルドおよび配置する方法が定義されます。 プロジェクト構成とは、プラットフォームおよびビルドの種類 (リリース Win32 など) に固有の一連のプロジェクト プロパティです。 これらの既定の構成を編集して、独自の構成を作成することもできます。 詳細については、「[プロジェクトおよびソリューションのプロパティの管理](managing-project-and-solution-properties.md)」を参照してください。  
  
 IDE 内で、次の追加タスクを実行することもできます。  
  
-   [ビルド出力ディレクトリを変更する](../ide/how-to-change-the-build-output-directory.md)。  
  
-   [正しくビルドするために、別のプロジェクトからの出力に依存するプロジェクトを特定する](../ide/how-to-create-and-remove-project-dependencies.md)。  
  
-   [ビルド ログまたはビルドの出力ウィンドウに含まれる情報の量を変更する](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
-   [Visual C#、Visual C++、または Visual Basic で特定のコンパイラの警告を非表示にする](../ide/how-to-suppress-compiler-warnings.md)。  
  
-   [ビルドに対してカスタムのコンパイル前アクションまたはコンパイル後アクションを指定する](../ide/specifying-custom-build-events-in-visual-studio.md)。  
  
-   並行ビルドを使用してビルド パフォーマンスを改善する。 詳細については、「[複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)」またはブログ投稿「[Tuning C++ build parallelism](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)」 (C++ での並列ビルドの調整) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: アプリケーションをビルドする](../ide/walkthrough-building-an-application.md)   
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [ビルド プラットフォームについて](../ide/understanding-build-platforms.md)   
 [Web サイト プロジェクトのビルド (コンパイル)](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   
 [方法 : プロジェクトの依存関係を作成および削除する](../ide/how-to-create-and-remove-project-dependencies.md)

---
title: "[必須コンポーネント] ダイアログ ボックス | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3d97e1f37c1e60c3ec5bb122a6b3f26c2fb086f9
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box

このダイアログ ボックスでは、必須コンポーネントとしてインストールするコンポーネント、そのインストール方法、およびパッケージのインストール順序を指定します。

このダイアログ ボックスを表示するには、**ソリューション エクスプローラー**でプロジェクト ノードを選択し、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。 **プロジェクト デザイナー** が表示されたら、 **[発行]** タブをクリックします。**[発行]** ページで、**[必須コンポーネント]** をクリックします。 セットアップ プロジェクトで、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。 **[プロパティ ページ]** ダイアログ ボックスが表示されたら、**[必須コンポーネント]** をクリックします。

## <a name="uielement-list"></a>UIElement の一覧

|要素|説明|
|-------------|-----------------|
|**必須コンポーネントをインストールするセットアップ プログラムを作成する**|必須コンポーネントをアプリケーションのセットアップ プログラム (Setup.exe) に含め、依存関係の順序に従って、それらのコンポーネントがアプリケーションより先にインストールされるようにします。 既定では、このチェック ボックスはオンになっています。 オフにした場合、Setup.exe は作成されません。|
|**インストールする必須コンポーネントを選択する**|[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]、Crystal Reports などのコンポーネントをインストールするかどうかを指定します。<br /><br /> たとえば、**[SQL Server 2005 Express Edition SP2]** の横のチェック ボックスをオンにした場合、セットアップ プログラムは、対象のコンピューターにこのコンポーネントがインストールされているかどうかを確認し、インストールされていなければインストールします。<br /><br /> 各必須パッケージの詳細については、後の「必須コンポーネント情報」を参照してください。|
|**再頒布可能コンポーネントについては、Microsoft Update を確認してください**|このリンクをクリックすると、[コンポーネントを再配布するための追加ブートストラップ パッケージ](http://go.microsoft.com/fwlink/?LinkId=208835)の Web サイトが表示されて、更新プログラムがあるかどうかを確認できます。|
|**必須コンポーネントをコンポーネントの開発元の Web サイトからダウンロードする**|販売元の Web サイトから必須コンポーネントをインストールするように指定します。 これは、既定の設定です。|
|**アプリケーションと同じ場所から必須コンポーネントをダウンロードする**|アプリケーションと同じ場所から必須コンポーネントをインストールするように指定します。 これにより、すべての必須パッケージが発行場所にコピーされます。 このオプションを使用するには、必須パッケージが開発用コンピューターに存在する必要があります。|
|**次の場所から必須コンポーネントをダウンロード**|選択した場所から必須コンポーネントをインストールするように指定します。 場所は、**[参照]** ボタンを使って指定できます。|

## <a name="prerequisites-information"></a>必須コンポーネント情報

**[必須コンポーネント]** ダイアログ ボックスに表示される必須コンポーネントは、後に示す一覧とは異なる場合があります。 **[必須コンポーネント] ダイアログ ボックス**にリストされている必須コンポーネントのパッケージは、ダイアログ ボックスを初めて開いたときに自動的に設定されます。 その後、プロジェクトのターゲット フレームワークを変更した場合は、新しいターゲット フレームワークに合わせて必須パッケージを手動で選択する必要があります。

|要素|説明|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|このパッケージは、次のコンポーネントをインストールします。<br /><br /> -  .NET Framework バージョン 2.0、3.0、および 3.5。<br />-   32 ビット (x86) オペレーティング システムおよび 64 ビット (x64) オペレーティング システム上の .NET Framework のすべてのバージョンに対するサポート。<br />-   パッケージと共にインストールされる各 .NET Framework バージョン用の Language Pack。<br />-   .NET Framework 2.0 および 3.0 用の Service Pack。<br /><br /> .NET Framework 3.0 は Windows Vista に含まれており、.NET Framework 3.5 は [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に含まれています。 .NET Framework 3.5 は、32 ビット オペレーティング システム用にコンパイルされる、ターゲット フレームワークが **.NET Framework 3.5** に設定された、すべての Visual Basic プロジェクトおよび C# プロジェクト、および、64 ビット オペレーティング システム用にコンパイルされる Visual Basic プロジェクトおよび C# プロジェクトに必要です。 IA64 はサポートされません。Visual Basic プロジェクトおよび C# プロジェクトは、既定ではどの CPU アーキテクチャにも対応するようにコンパイルされます。 詳細については、「[Visual Studio のマルチ ターゲットの概要](../../ide/visual-studio-multi-targeting-overview.md)」、および「[64 ビット アプリケーションの配置のための必要条件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)」を参照してください。<br /><br /> この項目は既定で選択されます。|
|**Microsoft .NET Framework 4.x**|このパッケージは、.NET Framework 4.x (x86 プラットフォームおよび x64 プラットフォーム用) をインストールします。|
|**Microsoft System CLR Types for SQL Server 2014 (x64 および x86)**|このパッケージは、Microsoft System CLR Types for SQL Server 2014 (x64 または x86 用) をインストールします。|
|**SQL Server 2008 R2 Express**|このパッケージは、Microsoft SQL Server 2008 R2 Express をインストールします。Microsoft SQL Server 2008 R2 Express は、Microsoft SQL Server 2008 R2 の無償のエディションであり、小規模な Web アプリケーション、サーバー アプリケーション、またはデスクトップ アプリケーションに最適なデータベースです。 Microsoft SQL Server 2008 Express は、開発環境および運用環境で無償で使用できます。 アプリケーションと共に SQL Server 2008 R2 Express を配布するには、無償の[登録](http://go.microsoft.com/fwlink/?LinkId=130380)が必要です。|
|**SQL Server 2012 Express**|このパッケージは、Microsoft SQL Server 2012 Express をインストールします。|
|**SQL Server 2012 Express LocalDB**|このパッケージは、Microsoft SQL Server 2012 Express LocalDB をインストールします。|
|**Visual C++ "14" ランタイム ライブラリ (ARM)**|Itanium アーキテクチャに対応する Visual C++ ランタイム ライブラリをインストールします。これらのライブラリは、Microsoft Windows オペレーティング システム用のプログラミング ルーチンを提供します。 これらのルーチンにより、C および C++ 言語では提供されない共通プログラミング タスクの多くを自動化できます。<br /><br /> 詳細については、「[C ランタイム ライブラリ リファレンス](/cpp/c-runtime-library/c-run-time-library-reference)」を参照してください。|
|**Visual C++ "14" ランタイム ライブラリ (x64)**|x64 オペレーティング システムに対応する Visual C++ ランタイム ライブラリをインストールします。これらのライブラリは、Microsoft Windows オペレーティング システム用のプログラミング ルーチンを提供します。 これらのルーチンにより、C および C++ 言語では提供されない共通プログラミング タスクの多くを自動化できます。<br /><br /> 詳細については、「[C ランタイム ライブラリ リファレンス](/cpp/c-runtime-library/c-run-time-library-reference)」を参照してください。|
|**Visual C++ "14" ランタイム ライブラリ (x86)**|x86 オペレーティング システムに対応する Visual C++ ランタイム ライブラリをインストールします。これらのライブラリは、Microsoft Windows オペレーティング システム用のプログラミング ルーチンを提供します。 これらのルーチンにより、C および C++ 言語では提供されない共通プログラミング タスクの多くを自動化できます。<br /><br /> 詳細については、「[C ランタイム ライブラリ リファレンス](/cpp/c-runtime-library/c-run-time-library-reference)」を参照してください。|

## <a name="see-also"></a>関連項目

[[発行] ページ (プロジェクト デザイナー)](../../ide/reference/publish-page-project-designer.md)  
[アプリケーション配置の必要条件](../../deployment/application-deployment-prerequisites.md)  
[64 ビット アプリケーションの配置のための必要条件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)  
[Visual Studio のマルチ ターゲットの概要](../../ide/visual-studio-multi-targeting-overview.md)

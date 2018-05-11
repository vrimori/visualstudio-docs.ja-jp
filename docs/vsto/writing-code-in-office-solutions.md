---
title: Office ソリューションでコードを記述 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6119db86fdd67079b63434a6bb494cb04cd31d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="writing-code-in-office-solutions"></a>Office ソリューションのコードの記述
  Office プロジェクトのコードの記述には、Visual Studio の他のプロジェクトの種類とは異なる点があります。 相違点の多くは、Office オブジェクト モデルがマネージ コードに公開される方法に関連しています。 Office プロジェクトのデザインに関連する相違点もあります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>マネージ コードおよび Office プログラミング  
 Microsoft Office 統合ソリューションの作成を実現するための鍵となるテクノロジは、コンポーネント オブジェクト モデル (COM: Component Object Model) テクノロジの一部であるオートメーションです。 オートメーションにより、コードを使用して、適切なプログラミング インターフェイスで作成されたアプリケーション、DLL、または ActiveX コントロールによって公開されるソフトウェア オブジェクトを作成および制御できます。  
  
### <a name="understanding-primary-interop-assemblies"></a>プライマリ相互運用機能アセンブリについて  
 Microsoft Office アプリケーションの多くの機能は、オートメーション用に公開されています。 ただし、マネージ コード (Visual Basic や C# など) を直接使用して Office アプリケーションを自動化することはできません。 マネージ コードを使用して Office アプリケーションを自動化するには、Office プライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を使用する必要があります。 プライマリ相互運用機能アセンブリにより、Office アプリケーションの COM ベースのオブジェクト モデルとマネージ コードとの相互運用を実行できるようになります。  
  
 すべての Microsoft Office アプリケーションに PIA があります。 Visual Studio で Office アプリケーションを作成すると、適切な PIA への参照が自動的にプロジェクトに追加されます。 プロジェクトから他の Office アプリケーションの機能を自動化するには、適切な PIA への参照を手動で追加する必要があります。 詳細については、「 [方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)」を参照してください。  
  
### <a name="using-primary-interop-assemblies-at-design-time-and-run-time"></a>デザイン時および実行時のプライマリ相互運用機能アセンブリの使用  
 ほとんどの開発タスクを実行するには、開発用コンピューターのグローバル アセンブリ キャッシュに Office PIA をインストールし、登録する必要があります。 詳細については、「 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)」を参照してください。  
  
 エンド ユーザーのコンピューターで [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とした Office ソリューションを実行する場合には、Office PIA は必要ありません。 詳細については、「 [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)」を参照してください。  
  
### <a name="using-types-in-primary-interop-assemblies"></a>プライマリ相互運用機能アセンブリでの型の使用  
 Office PIA には、Office アプリケーションのオブジェクト モデルを公開する型とコード内で直接使用することを目的としていない追加のインフラストラクチャの型の組み合わせが含まれています。 Office PIA の型の概要については、「 [Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5)」をご覧ください。  
  
 Office PIA の型は COM ベース オブジェクト モデルの型に対応しているため、これらの型の使用方法は、他のマネージ型の使用方法とは異なる場合があります。 たとえば、Office プライマリ相互運用機能アセンブリの省略可能なパラメーターを持つメソッドを呼び出す方法は、プロジェクトで使用するプログラミング言語によって異なります。 詳細については、次のトピックを参照してください。  
  
-   [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)です。  
  
-   [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md)」を参照してください。  
  
## <a name="programming-model-of-office-projects"></a>Office プロジェクトのプログラミング モデル  
 すべての Office プロジェクトには、コードのエントリ ポイントを提供する 1 つ以上のクラスが生成されます。 これらのクラスを使用して、ホスト アプリケーションのオブジェクト モデルにアクセスしたり、操作ウィンドウやカスタム作業ウィンドウなどの機能にアクセスしたりできます。  
  
### <a name="understanding-the-generated-classes"></a>生成されるクラスについて  
 Excel および Word のドキュメント レベル プロジェクトの場合、生成されるクラスは、アプリケーションのオブジェクト モデルのトップレベルのオブジェクトに似ています。 たとえば、Word 文書プロジェクトに生成される `ThisDocument` クラスは、Word オブジェクト モデルの <xref:Microsoft.Office.Interop.Word.Document> クラスと同じメンバーを提供します。 ドキュメント レベルのプロジェクトで生成されるクラスについて詳しくは、「 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)」をご覧ください。  
  
 VSTO アドイン プロジェクトには、 `ThisAddIn`というクラスが生成されます。 このクラスは、ホスト アプリケーションのオブジェクト モデル内のクラスには似ていません。 代わりに、このクラスは VSTO アドイン自体を表し、ホスト アプリケーションのオブジェクト モデルへのアクセスと、VSTO アドインで利用可能な他の機能へのアクセスに使用できるメンバーを提供します。詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 Office プロジェクトで生成されるすべてのクラスには、 `Startup` および `Shutdown` のイベント ハンドラーが含まれます。 コードを書き始めるには、通常はこれらのイベント ハンドラーにコードを追加します。 VSTO アドインを初期化するには、コードを `Startup` イベント ハンドラーに追加します。 VSTO アドインによって使用されるリソースをクリーンアップするには、コードを `Shutdown` イベント ハンドラーに追加します。 詳細については、「 [Events in Office Projects](../vsto/events-in-office-projects.md)」を参照してください。  
  
### <a name="accessing-the-generated-classes-at-run-time"></a>生成されたクラスへの実行時のアクセス  
 Office ソリューションが読み込まれると、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって、プロジェクト内に生成された各クラスがインスタンス化されます。 これらのオブジェクトには、プロジェクト内の任意のコードから `Globals` クラスを使用してアクセスできます。 たとえば、 `Globals` クラスを使用して、VSTO アドインのリボン ボタンのイベント ハンドラーから `ThisAddIn` クラスのコードを呼び出すことができます。  
  
 詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
### <a name="namespace-considerations-in-office-solutions"></a>Office ソリューションの名前空間に関する考慮事項  
 Office プロジェクトを作成した後で、プロジェクトの *既定の名前空間* (Visual Basic では *ルート名前空間* ) を変更することはできません。 既定の名前空間は、プロジェクトの作成時に指定したプロジェクト名と常に一致します。 プロジェクト名を変更しても、既定の名前空間は変更されません。 プロジェクトで既定の名前空間の詳細については、次を参照してください[アプリケーション ページで、プロジェクト デザイナー &#40;C&#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp)と[アプリケーション ページで、プロジェクト デザイナー &#40;Visual Basic&#41;](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="changing-the-namespace-of-host-item-classes-in-c-projects"></a>C# プロジェクトのホスト項目クラスの名前空間の変更  
 Visual C# Office プロジェクトの場合、ホスト項目クラス ( `ThisAddIn`、 `ThisWorkbook`、 `ThisDocument` などのクラス) は独自の名前空間を持ちます。 既定では、プロジェクトのホスト項目の名前空間は、プロジェクトの作成時に指定したプロジェクト名と一致します。  
  
 Visual C# Office プロジェクトのホスト項目の名前空間を変更するには、 **ホスト項目の名前空間** プロパティを使用します。 詳細については、次を参照してください。 [Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)です。  
  
## <a name="supported-programming-languages-in-office-projects"></a>Office プロジェクトでサポートされているプログラミング言語  
 Visual Studio の Office プロジェクト テンプレートは、プログラミング言語として Visual Basic と Visual C# のみサポートしています。 したがって、これらのプロジェクト テンプレートは、 **の** [新しいプロジェクト] **ダイアログ ボックスの** [Visual Basic] **ノードと** [Visual C#] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ノードでのみ使用できます。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
## <a name="language-choice-and-office-programming"></a>言語の選択と Office プログラミング  
 Microsoft Office と Visual Basic for Applications (VBA) には、相互の連携によってアプリケーションのカスタマイズ ワークフローを最適化する機能が組み込まれています。 そうした機能の一部は Visual Basic に引き継がれています。 たとえば、Visual Basic は省略可能なパラメーターをサポートしているため、Microsoft Office プライマリ相互運用機能アセンブリのメソッドを呼び出す場合、Visual C# よりコードが小さくなります。  
  
## <a name="programming-with-visual-basic-vs-visual-c-in-office-solutions"></a>Office ソリューションでの Visual Basic と Visual C# を使用したプログラミング  
 Office ソリューションは、Visual Basic と Visual C# のどちらを使用しても作成できます。 Microsoft Office オブジェクト モデルは VBA (Microsoft Visual Basic for Applications) で使用するようにデザインされているので、Visual Basic 開発者は Microsoft Office アプリケーションで公開されているオブジェクトを容易に操作できます。 Visual C# 開発者は Visual Basic 開発者と同じ機能のほとんどを使用できますが、Office オブジェクト モデルを使用するには、追加のコードを記述することが必要な場合があります。 また、Office 開発における基本的なプログラミング機能と Visual Basic や C# で記述されたマネージ コードとの間にもいくつかの違いがあります。  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Visual Basic と Visual C# の主な相違点  
 次の表は、Office 開発で Visual Basic を使用する場合と Visual C# を使用する場合の主な相違点を示しています。  
  
|機能|説明|Visual Basic のサポート|Visual C# のサポート|  
|-------------|-----------------|--------------------------|------------------------|  
|省略可能なパラメーター|Microsoft Office のメソッドには、呼び出すときに指定する必要のないパラメーターを持つメソッドが多数あります。 パラメーターの値を渡さない場合は、既定の値が使用されます。|Visual Basic では、省略可能なパラメーターをサポートしています。|Visual C# では、ほとんどの場合に省略可能なパラメーターをサポートしています。 詳細については、次を参照してください。 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)です。|  
|パラメーターの参照渡し|大部分の Microsoft Office プライマリ相互運用機能アセンブリにある省略可能なパラメーターは、値によって引き渡すこと (値渡し) ができます。 ただし、一部のプライマリ相互運用機能アセンブリでは、参照型を受け取る省略可能なパラメーターに対して参照渡しを行わなくてはなりません。<br /><br /> 値と参照型のパラメーターの詳細については、次を参照してください[値と参照渡しに引数を渡す&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic の場合) 用と[パラメーターの引き渡し&#40;C&#35; 。プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)です。|参照渡しでパラメーターを渡すのに、特別な処理は必要ありません。 Visual Basic コンパイラでは、必要に応じて自動的にパラメーターが参照渡しされます。|ほとんどの場合、Visual C# コンパイラでは、必要に応じて自動的にパラメーターが参照渡しされます。 詳細については、次を参照してください。 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)です。|  
|パラメーター化したプロパティ|プロパティの中には、パラメーターを受け取り、読み取り専用関数として動作するものがあります。|Visual Basic では、パラメーターを受け取るプロパティをサポートしています。|Visual C# では、パラメーターを受け取るプロパティをサポートしています。|  
|遅延バインディング|遅延バインディングでは、デザイン時にオブジェクトの型に変数をキャストするのではなく、実行時にオブジェクトのプロパティを決定します。|Visual Basic では、 **Option Strict** がオフの場合に遅延バインディングが実行されます。 ときに**Option Strict**オブジェクトとの使用の種類を明示的に変換する必要がありますが、上、<xref:System.Reflection>遅延バインディング メンバーにアクセスする名前空間。 詳細については、「 [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md)」を参照してください。|Visual C# では、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするプロジェクトで遅延バインディングが実行されます。 詳細については、「 [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md)」を参照してください。|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Office 開発とマネージ コードの主な相違点  
 次の表は、Office 開発と Visual Basic または Visual C# で作成されたマネージ コードの主な相違点を示しています。  
  
|機能|説明|Visual Basic および Visual C# のサポート|  
|-------------|-----------------|-----------------------------------------|  
|配列のインデックス|Microsoft Office アプリケーションでは、コレクションの配列の下限のインデックスは 1 から始まります。 Visual Basic や Visual C# では、インデックス番号が 0 から始まる配列が使用されます。 詳細については、次を参照してください。[配列&#40;C&#35;プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/arrays/index)と[Visual Basic における配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)です。|Microsoft Office アプリケーションのオブジェクト モデルのコレクションの 1 番目のアイテムにアクセスするには、インデックス 0 ではなく 1 を使用します。|  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)   
 [方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [方法: Office プロジェクトでイベント ハンドラーを作成します。](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)   
 [Office ソリューションの共同開発](../vsto/collaborative-development-of-office-solutions.md)  
  
  
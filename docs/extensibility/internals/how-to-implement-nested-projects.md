---
title: '方法: 入れ子になったプロジェクトの実施 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13993fca03afce3e14b5a016eba7924226c24b8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037838"
---
# <a name="how-to-implement-nested-projects"></a>方法: 入れ子になったプロジェクトを実装します。

入れ子になったプロジェクトの種類を作成するときに、いくつかの追加の手順を実装する必要があります。 親プロジェクトは、その入れ子になった (子) プロジェクトをソリューションに含まれている同様の役割の一部に対して実行します。 親プロジェクトは、ソリューションのようなプロジェクトのコンテナーです。 具体的には、入れ子になったプロジェクトの階層を構築する親プロジェクトおよびソリューションによって発生する必要がありますのあるいくつかのイベントがあります。 入れ子になったプロジェクトを作成するための次のプロセスでは、これらのイベントがについて説明します。

## <a name="create-nested-projects"></a>入れ子になったプロジェクトを作成します。

1.  統合開発環境 (IDE) では、親プロジェクトのプロジェクトのファイルとスタートアップの情報を読み込みます呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>インターフェイス。 親プロジェクトが作成され、ソリューションに追加します。

    > [!NOTE]
    > この時点では、子プロジェクトを作成する前に、親プロジェクトを作成する必要がありますので、入れ子になったプロジェクトを作成する親プロジェクトのプロセスには早すぎます。 このシーケンスでは、次の親プロジェクトは、子プロジェクトに設定を適用することができ、必要な場合、子プロジェクトは、親プロジェクトから情報を取得できます。 このシーケンスは、ソース コード管理 (SCC) などのクライアントに必要なかどうかと**ソリューション エクスプ ローラー**します。

     親プロジェクトに待つ必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>プロジェクトまたはプロジェクトの入れ子になった (子) を作成できる前に、IDE によって呼び出されるメソッド。

2.  IDE 呼び出し`QueryInterface`の親プロジェクトの<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>します。 この呼び出しが成功したかどうか、IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>すべて親プロジェクトの入れ子になったプロジェクトの起動の親のメソッド。

3.  親プロジェクトの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>プロジェクトを入れ子になったリスナーに通知するメソッドが作成されます。 たとえば、SCC、はソリューションとプロジェクトの作成プロセスの手順が順序で発生するかどうかを把握するこれらのイベントをリッスンします。 手順が順不同の発生した場合ソリューションが正しく登録されていないソース コード コントロールと。

4.  親プロジェクト呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>メソッドをそれぞれの子プロジェクト。

     渡す<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>を`AddVirtualProject`仮想 (入れ子になった) プロジェクトをビルドから除外するプロジェクト ウィンドウに追加する必要があることを示すメソッドが、ソース コード管理に追加します。 `VSADDVPFLAGS` 入れ子になったプロジェクトの表示を制御し、どのような機能が関連付けられていることを示すことができます。

     プロジェクト、親プロジェクトのプロジェクト ファイル、親プロジェクトの呼び出しに格納されている GUID を持つ既存の子プロジェクトを再読み込みする`AddVirtualProjectEx`します。 唯一の違い`AddVirtualProject`と`AddVirtualProjectEX`される`AddVirtualProjectEX`を指定する親プロジェクトを有効にするためのパラメーターをインスタンスごと`guidProjectID`子プロジェクトを有効にするため<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>関数正しくします。

     使用可能な GUID がないなど、ソリューション、プロジェクトのいずれかの作成を時に新しい入れ子になったプロジェクトを追加する場合は、親に追加されます。 そのプロジェクトのプロジェクト ファイルの GUID を保持する親プロジェクトの役目です。 入れ子になったプロジェクトを削除する場合、そのプロジェクトの GUID が削除もできます。

5.  IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren>親プロジェクトの場合は、各子プロジェクトのメソッド。

     親プロジェクトを実装する必要があります`IVsParentProject`プロジェクトの入れ子にする場合。 親のプロジェクトの呼び出しでは決して`QueryInterface`の`IVsParentProject`場合でも、その下にある親プロジェクトがあります。 ソリューションへの呼び出しを処理する`IVsParentProject`場合、その実装を呼び出すと、`OpenChildren`を入れ子になったプロジェクトを作成します。 `AddVirtualProjectEX` 必ず呼び出される`OpenChildren`します。 親プロジェクトの順序で、階層の作成のイベントを保持することはありません呼び出してください。

6.  IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>子プロジェクトでのメソッド。

7.  親プロジェクトの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>に親の子プロジェクトが作成されたことをリスナーに通知するメソッド。

8.  IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>親プロジェクトを後ですべての子プロジェクトが開かれているメソッド。

     親プロジェクトが呼び出すことで入れ子になったプロジェクトごとの GUID を作成するファイルは既に存在しない場合`CoCreateGuid`します。

    > [!NOTE]
    > `CoCreateGuid` GUID が作成されるときに、COM API が呼び出されます。 詳細については、次を参照してください。`CoCreateGuid`と MSDN ライブラリの Guid。

     親プロジェクトでは、この GUID は、次回の IDE で開かれたを取得するには、そのプロジェクト ファイルに格納します。 呼び出し元に関する詳細については、手順 4. を参照してください。`AddVirtualProjectEX`を取得する、`guidProjectID`子プロジェクト用。

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ItemID の親のメソッドが呼び出されます、慣例に委任することで、入れ子になったプロジェクトにします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>親で呼び出された場合に委任するプロジェクトをネストしているノードのプロパティを取得します。

     親と子プロジェクトがプログラムによってインスタンス化されるため、この時点で入れ子になったプロジェクトのプロパティを設定できます。

    > [!NOTE]
    > だけでなく、入れ子になったプロジェクトからコンテキスト情報を受け取ることは、親プロジェクトに、チェックしてその項目の任意のコンテキストが含まれるかどうかも要求できます<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>します。 この方法で、余分なダイナミック ヘルプの属性と固有のメニュー オプションを個別の入れ子になったプロジェクトに追加できます。

10. 表示、階層が構築された**ソリューション エクスプ ローラー**を呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>メソッド。

     階層を環境に渡す`GetNestedHierarchy`ソリューション エクスプ ローラーで表示するための階層を作成します。 この方法では、ソリューションは、プロジェクトが存在して構築するため、ビルド マネージャーで管理できますをソース コード管理下に配置するプロジェクト内のファイルを許可することができますを認識します。

11. Project1 の入れ子になったすべてのプロジェクトが作成されると、コントロールは、ソリューションに戻されます、Project2、プロセスが繰り返されます。

     入れ子になったプロジェクトを作成するためのこの同じプロセスでは、子がある子プロジェクトに対して発生します。 この場合、Project1 の子である、BuildProject1 子プロジェクトがある場合は作成する必要が BuildProject1 後と Project2 前にします。 プロセスは、再帰とダウン階層は上部から構築されます。

     入れ子になったプロジェクトを閉じる際に、ユーザーがソリューションを閉じているか、特定のプロジェクト自体、もう一方のメソッドであるため`IVsParentProject`、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>が呼び出されます。 親プロジェクトへの呼び出しをラップする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>ソリューション イベントをリスナーに入れ子になったプロジェクトが閉じられていることを通知するメソッド。

次のトピックでは、入れ子になったプロジェクトを実装する際に考慮するその他のいくつかの概念を処理します。

- [アンロード中で入れ子になったプロジェクトを再読み込みに関する考慮事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [入れ子になったプロジェクト ウィザードのサポート](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [入れ子になったプロジェクトのコマンド処理を実装します。](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [入れ子になったプロジェクトの [AddItem] ダイアログ ボックスをフィルター処理します。](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>関連項目

- [新しい項目の追加 ダイアログ ボックスに項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)
- [チェックリスト:新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)
- [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)
- [ウィザード (.vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)
---
title: '方法: 入れ子になったプロジェクトを実装して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c90434fd8deae2f5f71c150759fc836b9ed43077
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-implement-nested-projects"></a>方法: 入れ子になったプロジェクトを実装します。
作成する場合は、実装する必要があるいくつか追加の手順は、入れ子になったプロジェクトの種類があります。 親プロジェクトは、入れ子になった (子) プロジェクトのソリューションに含まれている同じ役割の一部で必要です。 親プロジェクトは、プロジェクトをソリューションと同様のコンテナーです。 具体的には、入れ子になったプロジェクトの階層を構築する親プロジェクトとソリューションによって発生する必要がありますをいくつかのイベントがあります。 入れ子になったプロジェクトを作成するための次のプロセスでは、これらのイベントが説明されています。

### <a name="to-create-nested-projects"></a>入れ子になったプロジェクトを作成するには

1.  統合開発環境 (IDE) では、親プロジェクトのプロジェクトのファイル サービスおよびスタートアップ情報を読み込みますを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>インターフェイスです。 親プロジェクトが作成され、ソリューションに追加します。

    > [!NOTE]
    >  この時点では、プロジェクトを作成する、入れ子になった子プロジェクトを作成する前に、親プロジェクトを作成する必要があるため、親プロジェクトのプロセスには古すぎますです。 このシーケンスでは、次の親プロジェクトは子プロジェクトに設定を適用することができ、必要な場合は、子プロジェクトは親プロジェクトからの情報を取得できます。 このシーケンスは、ソース コード管理 (SCC) やソリューション エクスプ ローラーなどのクライアントでの必要なかどうかです。

     親プロジェクトが待つ必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>のプロジェクトまたはその入れ子になった (子) を作成できる前に、IDE によって呼び出されるメソッド。

2.  IDE 呼び出し`QueryInterface`の親プロジェクトの<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>します。 かどうかはこの呼び出しが成功した、IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>を開くには、親プロジェクトの入れ子になったプロジェクトのすべての親のメソッドです。

3.  親プロジェクトから呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>プロジェクトを入れ子になったリスナーに通知するメソッドが作成されます。 SCC では、たとえばがリッスンしているこれらのイベントの順序で、ソリューションおよびプロジェクトの作成プロセスの手順が発生しているかどうかを知るにします。 手順が順不同が発生した場合、ソリューション可能性があります正しく登録されていないソース コード コントロールとします。

4.  親プロジェクトから呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>メソッドまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>メソッドをそれぞれの子プロジェクト。

     渡す<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>を`AddVirtualProject`プロジェクト ウィンドウで、ビルドから除外する仮想 (入れ子になった) プロジェクトを追加する必要があることを示すメソッドが、ソース コード管理に追加します。 `VSADDVPFLAGS` 入れ子にされたプロジェクトの可視性を管理し、どのような機能が関連付けられていることを示すことができます。

     プロジェクトは親プロジェクトのプロジェクト ファイルで、親プロジェクトから呼び出すに格納されている GUID を含む既存の子プロジェクトを再読み込みするかどうかは`AddVirtualProjectEx`します。 唯一の違い`AddVirtualProject`と`AddVirtualProjectEX`される`AddVirtualProjectEX`にパラメーターを指定する親プロジェクトを有効にする、インスタンスごと`guidProjectID`子プロジェクトを有効にするため<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>関数正しくです。

     ない場合の GUID、使用可能なソリューション、プロジェクトの 1 つの作成を時に新しい入れ子にされたプロジェクトを追加する場合などは、親に追加されます。 そのプロジェクトのプロジェクト ファイル内の GUID を保持する親プロジェクトの役割です。 入れ子にされたプロジェクトを削除すると、そのプロジェクトの GUID が削除もできます。

5.  IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren>親プロジェクトの場合は、各子プロジェクトでのメソッドです。

     親プロジェクトを実装する必要があります`IVsParentProject`プロジェクトを入れ子にする場合。 親のプロジェクトの呼び出しでは決して`QueryInterface`の`IVsParentProject`下にある親プロジェクトがある場合でもです。 ソリューションへの呼び出しを処理する`IVsParentProject`場合は、実装を呼び出すと、`OpenChildren`を入れ子になったプロジェクトを作成します。 `AddVirtualProjectEX` 常に呼び出される`OpenChildren`です。 親プロジェクトの順序で、階層の作成イベントを保持することはありません呼び出す必要があります。

6.  IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>子プロジェクトでのメソッドです。

7.  親プロジェクトから呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>メソッドに親の子プロジェクトが作成されたことをリスナーに通知します。

8.  IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>メソッドすべての子プロジェクトが開かれた後、親プロジェクト。

     親プロジェクトが呼び出すことで入れ子になったプロジェクトごとの GUID を作成、既にがない場合、`CoCreateGuid`です。

    > [!NOTE]
    >  `CoCreateGuid` GUID が作成されるときに COM API が呼び出されます。 詳細については、次を参照してください。`CoCreateGuid`と MSDN ライブラリの Guid。

     親プロジェクトは、IDE で開かれている次の時間を取得するには、そのプロジェクト ファイルでこの GUID を格納します。 呼び出しに関連する詳細については、手順 4. を参照してください`AddVirtualProjectEX`を取得する、`guidProjectID`子プロジェクト用。

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>親 ItemID のメソッドが呼び出されます慣例に委任することで、入れ子になったプロジェクトにします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>の親で呼び出された場合に委任するプロジェクトをネストしているノードのプロパティを取得します。

     親と子プロジェクトがプログラムによってインスタンス化されるため、この時点で入れ子になったプロジェクトのプロパティを設定できます。

    > [!NOTE]
    >  だけでなく、入れ子になったプロジェクトからコンテキスト情報を受信する操作を行いますが、親プロジェクトがチェックしてそのアイテムの任意のコンテキストを持つかどうかも要求できます<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>です。 ように、余分なダイナミック ヘルプの属性および固有のメニュー オプションを個別の入れ子になったプロジェクトに追加できます。

10. 呼び出しでソリューション エクスプ ローラーで表示するため、階層を構築、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>メソッドです。

     階層を環境に渡す`GetNestedHierarchy`ソリューション エクスプ ローラーで表示する階層を構築します。 この方法では、ソリューションは、プロジェクトが存在して、ビルド マネージャーでの構築に管理できますにソース コード管理の対象にするには、プロジェクト内のファイルを使用することができますを認識します。

11. Project1 の入れ子になったすべてのプロジェクトが作成されると、ソリューションに制御が渡されます、Project2、プロセスが繰り返されます。

     この同じプロセス入れ子になったプロジェクトを作成するのには、子を持っている子プロジェクトに対して発生します。 この場合、Project1 の子である、BuildProject1 に含まれる子プロジェクトがある場合は作成する必要が BuildProject1 後と Project2 前にします。 プロセスが再帰的、ダウン上部から、階層が作成されます。

     ユーザーがソリューションを閉じたか、特定のプロジェクト自体には、他のメソッドでは、入れ子にされたプロジェクトを閉じる際に`IVsParentProject`、<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>と呼びます。 親プロジェクトへの呼び出しをラップする、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>の入れ子になったプロジェクトが切断されているソリューションのイベントをリスナーに通知するメソッド。

 次のトピックは、入れ子になったプロジェクトを実装する際に考慮するその他のいくつかの概念を処理します。

 [入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)

 [入れ子になったプロジェクト向けのウィザード サポート](../../extensibility/internals/wizard-support-for-nested-projects.md)

 [入れ子になったプロジェクト向けのコマンド処理の実装](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)

 [入れ子になったプロジェクトのための [AddItem] ダイアログ ボックスのフィルター処理](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>関連項目

- [[新しい項目の追加] ダイアログ ボックスへの項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)
- [チェック リスト: 新しいプロジェクト タイプの作成](../../extensibility/internals/checklist-creating-new-project-types.md)
- [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)
- [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)
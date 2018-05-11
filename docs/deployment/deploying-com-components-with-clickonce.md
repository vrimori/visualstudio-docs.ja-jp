---
title: ClickOnce での COM コンポーネントを展開する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 740d72f0ec339ded8ec8b721bbc2b94d706f8da7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="deploying-com-components-with-clickonce"></a>ClickOnce での COM コンポーネントの配置
従来の COM コンポーネントの展開には、難しい作業されていましたが。 コンポーネントは、グローバルに登録される必要があるし、したがって重複しているアプリケーション間では、望ましくない副作用が発生することができます。 この状況は通常、.NET Framework アプリケーションに問題があるコンポーネントをアプリケーションに完全に分離されたか、サイド バイ サイド互換であるためです。 Visual Studio では、Windows XP または以上のオペレーティング システムで分離されている COM コンポーネントを展開することができます。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET アプリケーションを展開するための簡単かつ安全なメカニズムを提供します。 ただし、アプリケーションでは、従来の COM コンポーネントを使用する場合は、それらを展開するための追加の手順を実行する必要があります。 このトピックでは、分離された COM コンポーネントを展開し、(たとえば、Visual Basic 6.0 または Visual C) からネイティブ コンポーネントを参照する方法について説明します。  
  
 分離された COM コンポーネントを展開する方法の詳細については、次を参照してください。"でアプリの展開を簡略化する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]と登録を必要としない COM"で[ http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)です。  
  
## <a name="registration-free-com"></a>登録を必要としない COM  
 登録を必要としない COM は、展開および分離 COM コンポーネントをアクティブ化するための新しいテクノロジです。 でも、すべてのコンポーネントのタイプ ライブラリと、マニフェストと呼ばれる XML ファイルにシステム レジストリに通常インストールされている登録情報を記述することによって、アプリケーションと同じフォルダーに格納します。  
  
 COM コンポーネントを分離するには、開発者のコンピューターに登録することが必要ですが、エンドユーザーのコンピューターに登録する必要はありません。 COM コンポーネントで特定するのに行う必要がある設定の参照の**Isolated**プロパティを**True**です。 既定では、このプロパティに設定**False**、登録されている COM 参照として処理する必要があることを示すです。 このプロパティは、する場合**True**ビルド時にこのコンポーネントに対して生成されるマニフェストします。 これもにより、対応するファイルのインストール時に、アプリケーションのフォルダーにコピーします。  
  
 すべての列挙マニフェスト ジェネレーターには、分離の COM 参照が検出されると、ときに、`CoClass`に対応する登録データ、各エントリに一致して、生成するコンポーネントのタイプ ライブラリ内のエントリのマニフェストのすべての COM の定義タイプ ライブラリ ファイル内のクラス。  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>ClickOnce を使用して登録を必要としない COM コンポーネントを展開します。  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置テクノロジは、最適な分離の COM コンポーネントの配置のため両方[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]コンポーネントがある展開するために、マニフェストの登録を必要としない COM を必要とします。  
  
 通常、コンポーネントの作成者はマニフェストを提供する必要があります。 それ以外の場合は、ただし、Visual Studio は、COM コンポーネントを自動的にマニフェストを生成できます。 マニフェストの生成の実行中に、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]公開のプロセスです。 詳細については、次を参照してください。 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)です。 この機能では、Visual Basic 6.0 などの以前の開発環境で作成したレガシ コンポーネントを活用することもできます。  
  
 2 つの方法を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]COM コンポーネントを展開します。  
  
-   ブートス トラップを使用して、COM コンポーネントを展開するにはこれは、サポートされているすべてのプラットフォームで動作します。  
  
-   ネイティブ コンポーネントの分離 (登録を必要としない COM とも呼ばれます) の展開を使用します。 ただし、この方法は、Windows XP または以上のオペレーティング システムでのみ動作します。  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>分離と単純な COM コンポーネントの配置の例  
 登録を必要としない COM コンポーネントの配置を実行するために次の例が Visual Basic 6.0 を使用して作成された分離ネイティブ COM コンポーネントを参照している Visual Basic での Windows ベースのアプリケーションを作成および展開を使用して[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]です。  
  
 まず、ネイティブな COM コンポーネントを作成する必要があります。  
  
##### <a name="to-create-a-native-com-component"></a>ネイティブな COM コンポーネントを作成するには  
  
1.  Visual Basic 6.0 を使用して、**ファイル** メニューのをクリックして**新規**、し**プロジェクト**です。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**ノードを選択、 **ActiveX DLL**プロジェクト。 **[名前]** ボックスに「`VB6Hello`」と入力します。  
  
    > [!NOTE]
    >  登録を必要としない COM; でのみと ActiveX コントロールを ActiveX DLL プロジェクトの種類がサポートされています。ActiveX EXE および ActiveX ドキュメント プロジェクトの種類はサポートされていません。  
  
3.  **ソリューション エクスプ ローラー**をダブルクリックして**Class1.vb**テキスト エディターを開きます。  
  
4.  Class1.vb で生成されたコードの後に次のコードを追加、`New`メソッド。  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  コンポーネントをビルドします。 **ビルド** メニューをクリックして**ソリューションのビルド**です。  
  
> [!NOTE]
>  登録を必要としない COM が Dll のみをサポートし、COM は、プロジェクトの種類を制御します。 登録を必要としない COM の exe ファイルを使用することはできません。  
  
 今すぐ Windows ベースのアプリケーションを作成したり、COM コンポーネントへの参照を追加しています。  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>COM コンポーネントを使用して Windows ベースのアプリケーションを作成するには  
  
1.  Visual Basic を使用して、**ファイル** メニューのをクリックして**新規**、し**プロジェクト**です。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**ノード**Windows アプリケーション**です。 **[名前]** ボックスに「`RegFreeComDemo`」と入力します。  
  
3.  **ソリューション エクスプ ローラー**、] をクリックして、 **[すべてのファイル**プロジェクト参照を表示するボタンをクリックします。  
  
4.  右クリックし、**参照**ノード**参照の追加**コンテキスト メニュー。  
  
5.  **参照の追加**ダイアログ ボックスで、をクリックして、**参照** タブ、VB6Hello.dll に移動し、それを選択します。  
  
     A **VB6Hello**参照、参照の一覧に表示されます。  
  
6.  をポイント、**ツールボックス**、select、**ボタン**コントロール、ドラッグして、 **Form1**フォーム。  
  
7.  **プロパティ**ウィンドウで、設定、ボタンの**テキスト**プロパティを**こんにちは**です。  
  
8.  ハンドラー コードを追加するには、ボタンをダブルクリックし、コード ファイルで、ハンドラーを次のように読み取るようにするにコードを追加します。  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. アプリケーションを実行します。 **デバッグ** メニューのをクリックして**デバッグの開始**です。  
  
 次にコントロールを分離する必要があります。 アプリケーションで使用される各 COM コンポーネントは、COM 参照としてプロジェクトで表されます。 これらの参照は下に表示される、**参照**内のノード、**ソリューション エクスプ ローラー**ウィンドウです。 (直接を使用するかを参照して追加することに注意してください、**参照の追加**コマンドを**プロジェクト**メニュー、または ActiveX コントロールをフォームにドラッグして直接)。  
  
 次の手順では、COM コンポーネントを分離し、分離のコントロールを含む更新されたアプリケーションを公開する方法を示します。  
  
##### <a name="to-isolate-a-com-component"></a>COM コンポーネントを分離するには  
  
1.  **ソリューション エクスプ ローラー**で、**参照**ノードで、選択、 **VB6Hello**参照します。  
  
2.  **プロパティ**ウィンドウの値を変更、 **Isolated**プロパティから**False**に**True**です。  
  
3.  **ビルド** メニューをクリックして**ソリューションのビルド**です。  
  
 ここで、アプリケーションが動作を予想どおり、f5 キーを押してものの、ときの登録を必要としない COM で実行されるようになりました これを証明するために VB6Hello.dll コンポーネントの登録を解除し、Visual Studio IDE の外部で RegFreeComDemo1.exe を実行してください。 ボタンがクリックされたときに、この時間にも機能します。 アプリケーション マニフェストを一時的に変更する場合、もう一度は失敗します。  
  
> [!NOTE]
>  COM コンポーネントがない場合をシミュレートするには、一時的にその登録を解除します。 コマンド プロンプトを開き、」と入力して、システム フォルダーに移動`cd /d %windir%\system32`、」と入力して、コンポーネントの登録を解除`regsvr32 /u VB6Hello.dll`です。 」と入力してもう一度登録することができます`regsvr32 VB6Hello.dll`です。  
  
 最後の手順を使用して、アプリケーションを発行する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>分離 COM コンポーネントとアプリケーションの更新プログラムを発行するには  
  
1.  **ビルド** メニューのをクリックして**発行 RegFreeComDemo**です。  
  
     発行ウィザードが表示されます。  
  
2.  発行ウィザードでは、ローカル コンピューターのディスクにアクセスして、発行されたファイルを調査できます場所を指定します。  
  
3.  をクリックして**完了**でアプリケーションを公開します。  
  
 発行されたファイルを確認することは sysmon.ocx ファイルが含まれることがわかります。 コントロールがエンドユーザーのコンピューターに、コントロールの別のバージョンを使用して別のアプリケーションがある場合はこのアプリケーションに干渉できないので、このアプリケーションに完全に分離されています。  
  
## <a name="referencing-native-assemblies"></a>ネイティブ アセンブリの参照  
 Visual Studio は、ネイティブの Visual Basic 6.0 または C++ アセンブリへの参照をサポートしています。このような参照は、ネイティブ参照と呼ばれます。 確認することにより、参照がネイティブかどうかを指定することができます、**ファイルの種類**プロパティに設定されている**ネイティブ**または**ActiveX**です。  
  
 ネイティブ参照を追加するには、使用、**参照の追加**コマンドを使用し、マニフェストを参照します。 一部のコンポーネントは、DLL 内に、マニフェストを配置します。 ここでは、DLL 自体を選択するだけ Visual Studio は、追加し、ネイティブ参照として、コンポーネントに埋め込まれたマニフェストが含まれていることが検出された場合。 Visual Studio には、任意の依存ファイルまたはアセンブリの参照先のコンポーネントと同じフォルダー内にある場合、マニフェストに示さがも自動的に含まれます。  
  
 COM コントロールを分離しやすくマニフェストがない COM コンポーネントを展開します。 ただし、コンポーネントは、指定した場合、マニフェストを伴う、マニフェストを直接参照できます。 使用するのではなく可能な限り、コンポーネントの作成者によって指定されたマニフェストを使用するは常に実際には、 **Isolated**プロパティです。  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>登録しない COM コンポーネントの配置の制限事項  
 登録を必要としない COM では、従来の展開方法にクリアの利点を提供します。 ただしは、いくつかの制限事項とする必要がありますも指摘注意事項があります。最大の制限は、のみ動作する Windows XP またはそれ以上です。 登録を必要としない COM の実装には、コア オペレーティング システムのコンポーネントが読み込まれているように変更が必要です。 残念ながら、登録を必要としない COM のダウン レベルのサポートのレイヤーがありません。  
  
 すべてのコンポーネントが登録を必要としない COM の適切な候補 コンポーネントは、次のいずれかに当てはまる場合、適切な。  
  
-   コンポーネントは、アウト プロセス サーバーです。 EXE サーバーはサポートされていません。Dll のみがサポートされます。  
  
-   コンポーネントは、オペレーティング システムの一部であるか、XML、Internet Explorer、Microsoft Data Access Components (MDAC) などのシステム コンポーネントがします。 コンポーネント作成者の再配布ポリシーに従う必要があります。ベンダーに確認します。  
  
-   コンポーネントは、Microsoft Office などのアプリケーションの一部です。 たとえば、Microsoft Excel オブジェクト モデルを分離するはされません。 これは、Office の一部であるし、はことができますのみ併用コンピューターでフル Office 製品がインストールされてです。  
  
-   コンポーネントは、アドインまたはスナップインで、Office アドインなど、Web ブラウザー内のコントロールとして使用するものです。 このようなコンポーネントには、ある種の登録のスキームは扱いませんが、マニフェスト自体をホスト環境によって定義された通常必要があります。  
  
-   コンポーネントは、印刷スプーラのデバイス ドライバーなど、システムの物理または仮想デバイスを管理します。  
  
-   コンポーネントは、再頒布可能パッケージのデータ アクセスです。 データ アプリケーションには、通常、独立したデータへのアクセス再頒布可能パッケージを実行する前にインストールするが必要です。 Microsoft ADO データ コントロール、Microsoft OLE DB、または Microsoft Data Access Components (MDAC) などのコンポーネントを分離しようとする必要があります。 代わりに、アプリケーションは、MDAC または SQL Server Express を使用する場合としてを設定に前提条件です。参照してください[する方法: ClickOnce アプリケーションと共に必須コンポーネントをインストール](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)です。  
  
 場合によっては、コンポーネントの開発者は、登録を必要としない COM の再設計の考えられる場合があります。 これが可能でない場合もビルドし、ブートス トラップを使用して標準的な登録スキームを通じてそれらに依存するアプリケーションを公開します。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)です。  
  
 COM コンポーネントは、1 つのアプリケーション分離 1 回のみ指定できます。 たとえば、2 つの異なるから、同じ COM コンポーネントを分離することはできません**クラス ライブラリ**プロジェクトは、同じアプリケーションの一部であります。 これを行うとビルドの警告が発生し、アプリケーションの実行時に読み込みが失敗します。 この問題を回避するためには、マイクロソフトは、1 つのクラス ライブラリ内の COM コンポーネントをカプセル化することをお勧めします。  
  
 Com 登録が、開発者のコンピューターに必要ないくつかのシナリオがある場合でも、アプリケーションの配置には、登録は不要です。 `Isolated`プロパティは、ビルド時にマニフェストを自動生成するために、開発者のマシンに COM コンポーネントを登録が必要です。 ビルド時に自己登録を呼び出す登録キャプチャ機能はありません。 また、タイプ ライブラリで明示的に定義されているすべてのクラスは、マニフェストには反映されません。 ネイティブ参照などの既存のマニフェストを伴う、COM コンポーネントを使用して、コンポーネントでは、開発時に登録する必要はありません。 ただし、登録は、必要なコンポーネントは、ActiveX コントロールを含めるようにする場合、**ツールボックス**と Windows フォーム デザイナー。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)
---
title: Office ソリューションの特定のセキュリティに関する考慮事項
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7da9446a4a5e4538164b09d1f11733f7bde3de24
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693358"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office ソリューションの特定のセキュリティに関する考慮事項
  Microsoft .NET Framework および Microsoft Office には、Office ソリューションをセキュリティ上の脅威から保護するためのセキュリティ機能が備わっています。 このトピックでは、このような脅威のいくつかについて説明し、脅威対策に関する推奨事項を示します。 また、Microsoft Office のセキュリティ設定が Office ソリューションに及ぼす影響についても説明します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>信頼されたコードが悪意のある、新しいドキュメントで再利用します。  
 攻撃者は、たとえば、個人情報をダウンロードするための雇用アプリケーションのコードなど、ある特定の用途のための信頼されたコードを取得し、ワークシートなどの別のドキュメントでそのコードを再利用する可能性があります。 コードは元のドキュメントが実行されていないことを認識しないため、別のユーザーが開いた場合に他の脅威 (個人情報の漏洩や拡大された権限によるコードの実行など) を招くことがあります。 あるいは、攻撃者は単にワークシートのデータを、被害者に送信されたときに予期しない動作を実行するように変更することもできます。 悪意を持つユーザーは、コードにリンクされているワークシートの値、数式、または表示特性を変更して、変更後のファイルを送りつけて別のユーザーを攻撃する可能性があります。 また、ワークシートの値を修正して、許可されていない情報にアクセスすることもできます。  
  
 実行するには、アセンブリの位置とドキュメントの位置の両方の証拠が十分でなければならないため、このような攻撃は簡単には実行できません。 たとえば、電子メール添付ファイルのドキュメントや信頼されていないイントラネット サーバーのドキュメントには、実行に必要なアクセス許可がありません。  
  
 このような攻撃を可能にするには、コード自体が、信頼できない可能性のあるデータに基づいて決定を下すように作成されていなければなりません。 たとえば、非表示のセルにデータベース サーバーの名前を含むワークシートを作成するとします。 ユーザーがこのワークシートを ASPX ページに送信すると、SQL 認証およびハードコーディングされた SA パスワードを使用してそのサーバーに接続しようとします。 攻撃者は、非表示のセルの内容を別のコンピューター名に置き換え、SA パスワードを取得する可能性があります。 このような問題を回避するために、絶対にパスワードはハードコーディングしないでください。また、サーバーにアクセスする前に、必ず、既知の信頼できるサーバーを示す内部リストでそのサーバー ID を確認してください。  
  
### <a name="recommendations"></a>推奨事項  
  
-   入力内容およびデータのソースが、ユーザー、ドキュメント、データベース、Web サービス、その他のソースのどれであるかを常に確認してください。  
  
-   特定の種類の機能を公開する場合には、注意が必要です。たとえば、権限の設定されたデータをユーザーに代わって取得し、保護されていないワークシートにこのデータを挿入する場合に注意が必要となります。  
  
-   アプリケーションの種類によっては、元のドキュメントが実行されていることを検証してからコードを実行することが有効な対策になります。 たとえば、既知の安全な場所に保存されているドキュメントから実行されていることを検証します。  
  
-   権限の設定されたアクションを実行するアプリケーションの場合は、ドキュメントを開くときに警告メッセージを表示することをお勧めします。 たとえば、アプリケーションが個人情報にアクセスすることを知らせるスプラッシュ スクリーンやスタートアップのダイアログ ボックスを作成して、ユーザーに操作の続行またはキャンセルを選択してもらうことができます。 エンド ユーザーは、一見無害なドキュメントからこのような警告が表示された場合に、情報が漏洩する前にアプリケーションを終了できます。  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>コードが Outlook オブジェクト モデルの保護によってブロックされています。  
 Microsoft Office では、オブジェクト モデルの特定のプロパティ、メソッド、およびオブジェクトをコードで使用できないように制限できます。 これらのオブジェクトへのアクセスを制限では、Outlook は、悪意のある目的のオブジェクト モデルを使用して電子メール ワームやウイルスを防ぐのに役立ちます。 このセキュリティ機能は、Outlook オブジェクト モデルの保護と呼ばれています。 オブジェクト モデルの保護が有効になっているときに、制限されているプロパティまたはメソッドを VSTO アドインが使用しようとすると、Outlook はセキュリティ警告を表示します。これを受けてユーザーは、操作を中断したり、一定の時間内だけプロパティまたはメソッドへのアクセス許可を与えたりできます。 ユーザーが操作を中断した場合、Visual Studio で Office ソリューションを使用して作成された Outlook VSTO アドインは <xref:System.Runtime.InteropServices.COMException>をスローします。  
  
 オブジェクト モデルの保護の対象にできる VSTO アドインは、Outlook を Microsoft Exchange Server と併用しているかどうかに応じて、次のように異なります。  
  
-   Outlook を Exchange と併用していない場合、管理者は、コンピューター上のすべての VSTO アドインを対象として、オブジェクト モデルの保護を有効または無効にできます。  
  
-   Outlook を Exchange と併用している場合、管理者は、コンピューター上のすべての VSTO アドインを対象としてオブジェクト モデルの保護を有効または無効にできるのに加え、オブジェクト モデルの保護の対象外として動作させる特定の VSTO アドインを指定できます。 また、管理者は、オブジェクト モデルの特定の領域でのオブジェクト モデルの保護の動作を変更することもできます。 たとえば、オブジェクト モデルの保護が有効になっている場合でも、管理者は、VSTO アドインをプログラムでは、電子メールの送信を許可自動的にできます。  
  
 Outlook 2007 以降、オブジェクト モデルの保護の動作は、Outlook のセキュリティを維持しながらも、開発者やユーザー エクスペリエンスを向上させるように変更されています。 詳細については、次を参照してください。 [Outlook 2007 におけるセキュリティの変更をコード](http://go.microsoft.com/fwlink/?LinkId=73429)です。  
  
### <a name="minimize-object-model-guard-warnings"></a>オブジェクト モデルの保護の警告を最小限に抑える  
 制限されたプロパティおよびメソッドを使用したときのセキュリティ警告を回避するには、VSTO アドインで、Outlook オブジェクトをプロジェクト内の `Application` クラスの `ThisAddIn` フィールドから取得するようにします。 このフィールドの詳細については、次を参照してください。[プログラムは、VSTO アドイン](../vsto/programming-vsto-add-ins.md)です。  
  
 オブジェクト モデルの保護が信頼するのは、このオブジェクトから取得された Outlook オブジェクトのみです。 これに対し、オブジェクトを新しく取得される`Microsoft.Office.Interop.Outlook.Application`オブジェクトは信頼されていないと、制限されたプロパティとメソッド セキュリティ警告が発生してオブジェクト モデルの保護が有効になっている場合。  
  
 次のコード例は、オブジェクト モデルの保護が有効になっている場合に、セキュリティの警告を表示します。 `To`のプロパティ、`Microsoft.Office.Interop.Outlook.MailItem`クラスは、オブジェクト モデルの保護によって制限されます。 `Microsoft.Office.Interop.Outlook.MailItem`からのコードを取得するため、オブジェクトに信頼されていない、`Microsoft.Office.Interop.Outlook.Application`を使用して作成された、**新しい**から取得するのではなく、演算子、`Application`フィールドです。  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 次のコード例を使用して、制限する方法のプロパティを示しています、`Microsoft.Office.Interop.Outlook.MailItem`オブジェクト モデルの保護によって信頼されているオブジェクト。 コードを使用して、信頼されている`Application`を取得するフィールド、`Microsoft.Office.Interop.Outlook.MailItem`です。  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Outlook を Exchange と併用している場合、すべての Outlook オブジェクトを `ThisAddIn.Application` から取得しても、VSTO アドインが Outlook オブジェクト モデル全体にアクセスできるとは限りません。 たとえば、Exchange 管理者の Outlook からの自動的に設定する場合を拒否する、Outlook オブジェクト モデルを使用してアドレス情報にアクセスするすべての試行場合でも、このコード例では、Outlook に To プロパティにアクセスする前のコード例は許可しない、信頼`ThisAddIn.Application`フィールドです。  
  
### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Exchange を使用する場合を信頼するアドインを指定します。  
 Outlook を Exchange と併用している場合、管理者は、オブジェクト モデルの保護の対象外として動作させる特定の VSTO アドインを指定できます。 Visual Studio で Office ソリューションを使用して作成した個別の Outlook VSTO アドインは信頼できません。これらはグループとしてのみ信頼できます。  
  
 Outlook は、VSTO アドインのエントリ ポイント DLL のハッシュ コードに基づいて VSTO アドインを信頼します。 すべて Outlook VSTO アドインを対象とする、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]同じエントリ ポイント DLL を使用して (*VSTOLoader.dll*)。 つまり、管理者が、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をターゲットとする VSTO アドインを信頼してオブジェクト モデルの保護の対象外として動作させる場合、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をターゲットとする他のすべての VSTO アドインも併せて信頼されます。 特定の VSTO アドインを信頼してオブジェクト モデルの保護の対象外として動作させる方法の詳細については、 [「Outlook でウイルス対策機能を管理するために使用する方法を指定する」](http://go.microsoft.com/fwlink/?LinkId=128773)を参照してください。  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>アクセス許可の変更は反映されません直ちに  
 管理者がドキュメントまたはアセンブリのアクセス許可を調整した場合、それらの調整を適用させるには、ユーザーがすべての Office アプリケーションを終了して再起動する必要があります。  
  
 Microsoft Office アプリケーションをホストする他のアプリケーションが原因で、新しいアクセス許可が適用されない場合もあります。 セキュリティ ポリシーが変更された場合、ユーザーは Office を使用するすべてのアプリケーションを (ホストされているか、スタンドアロンであるかを問わず) 終了してください。  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office system で信頼センターの設定には影響しませんアドインまたはドキュメント レベルのカスタマイズ  
 ユーザーは、 **セキュリティ センター**でオプションを設定して、VSTO アドインの読み込みを禁止できます。 ただし、Visual Studio で Office ソリューションを使用して作成される VSTO アドインとドキュメント レベルのカスタマイズには、これらのセキュリティ設定は影響しません。  
  
 **セキュリティ センター**を使用して VSTO アドインの読み込みを禁止した場合、次のタイプのアドインは読み込まれません。  
  
-   マネージ COM VSTO アドインおよびアンマネージ COM VSTO アドイン。  
  
-   マネージ スマート ドキュメントおよびアンマネージ スマート ドキュメント。  
  
-   マネージ オートメーション VSTO アドインおよびアンマネージ オートメーション VSTO アドイン。  
  
-   マネージ リアルタイム データ コンポーネントおよびアンマネージ リアルタイム データ コンポーネント。  
  
 次の手順では、ユーザーが **[セキュリティ センター]** を使用して、Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] および Microsoft Office 2010 で VSTO アドインの読み込みを制限する方法について説明します。 これらの手順は、Visual Studio で Office 開発ツールを使用して作成された VSTO アドインまたはカスタマイズには影響しません。  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Microsoft Office 2010 および Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] アプリケーションの VSTO アドインを無効にするには  
  
1.  **[ファイル]** タブを選択します。  
  
2.  *[ApplicationName* **オプション]** ボタンを選択します。  
  
3.  [カテゴリ] ウィンドウで **[セキュリティ センター]** を選択します。  
  
4.  詳細ウィンドウで **[セキュリティ センターの設定]** を選択します。  
  
5.  [カテゴリ] ウィンドウで **[アドイン]** を選択します。  
  
6.  詳細ウィンドウで **[アプリケーション アドインに対し、信頼できる発行元の署名を必須にする]** または **[すべてのアプリケーション アドインを無効にする]** を選択します。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)  
  
  
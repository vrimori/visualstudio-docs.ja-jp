---
title: "[サービス参照の構成] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "WCF サービス、[サービス参照の構成] ダイアログ ボックス"
  - "サービス参照 [Visual Studio]、動作の構成"
  - "[サービス参照の構成] ダイアログ ボックス"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# [サービス参照の構成] ダイアログ ボックス
**\[サービス参照の構成\]** ダイアログ ボックスでは、[!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] サービスの動作を構成できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、\[ツール\] メニューの \[設定のインポートとエクスポート\] をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **\[サービス参照の構成\]** ダイアログ ボックスにアクセスするには、**ソリューション エクスプローラー** でサービス参照を右クリックし、**\[サービス参照の構成\]** を選択します。  [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)で **\[詳細\]** ボタンをクリックしてダイアログ ボックスにアクセスすることもできます。  
  
## タスク一覧  
  
-   WCF サービスがホストされるアドレスを変更するには、**\[アドレス\]** フィールドに新しいアドレスを入力します。  
  
-   WCF クライアント内のクラスのアクセス レベルを変更するには、**\[生成されたクラスのアクセス レベル\]** リストでアクセス レベル キーワードを選択します。  
  
-   WCF サービスのメソッドを非同期に呼び出すには、**\[非同期操作を生成する\]** チェック ボックスをオンにします。  
  
-   WCF クライアントでメッセージ コントラクト型を生成するには、**\[メッセージ コントラクトを常に生成\]** チェック ボックスをオンにします。  
  
-   WCF クライアントのリストまたはディクショナリ コレクションの型を指定するには、**\[コレクション型\]** リストおよび **\[ディクショナリ コレクション型\]** リストから型を選択します。  
  
-   型の共有を無効にするには、**\[参照されたアセンブリで型を再利用\]** チェック ボックスをオフにします。  参照されたアセンブリのサブセットで型の共有を有効にするには、**\[参照されたアセンブリで型を再利用\]** チェック ボックスをオンにし、**\[参照されたアセンブリを指定して型を再利用\]**チェック ボックスをオンにして、**\[Referenced assemblies list \(参照されたアセンブリ一覧\)\]** で必要な参照を選択します。  
  
## UIElement の一覧  
 **Address**  
 サービス参照がサービスを検索する Web アドレスを更新するために使用されます。  たとえば、開発中のサービスは開発サーバーでホストされ、その後、運用サーバーに移されることがあり、アドレスの変更が必要になります。  
  
> [!NOTE]
>  Address 要素は、**\[サービス参照の構成\]** ダイアログ ボックスが [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)から表示された場合は使用できません。  
  
 **\[生成されたクラスのアクセス レベル\]**  
 WCF クライアント クラスのコード アクセス レベルを特定します。  
  
> [!NOTE]
>  Web サイト プロジェクトの場合、このオプションは常に `Public` に設定され、変更できません。  詳細については、「[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)」を参照してください。  
  
 **\[非同期操作を生成する\]**  
 WCF サービス メソッドの呼び出しが同期 \(既定\) または非同期のどちらであるかを指定します。  
  
 **\[タスク ベースの操作を生成する\]**  
 非同期コードを作成する場合、このオプションにより、.Net 4 で導入されたタスク並列ライブラリ \(TPL\) を利用できます。  「[タスク並列ライブラリ \(TPL\)](http://msdn.microsoft.com/library/dd460717.aspx)」を参照してください。  
  
 **\[メッセージ コントラクトを常に生成\]**  
 WCF クライアント向けにメッセージ コントラクト型が生成されるかどうかを指定します。  メッセージ コントラクトの詳細については、「[メッセージ コントラクトの使用](../Topic/Using%20Message%20Contracts.md)」を参照してください。  
  
 **\[コレクション型\]**  
 WCF クライアントのリスト コレクション型を指定します。  既定の型は <xref:System.Array> です。  
  
 **\[ディクショナリ コレクション型\]**  
 WCF クライアントのディクショナリ コレクション型を指定します。  既定の型は <xref:System.Collections.Generic.Dictionary%602> です。  
  
 **\[参照されたアセンブリで型を再利用\]**  
 サービスが追加または更新された場合、WCF クライアントが、新しい型を生成する代わりに、参照されたアセンブリ内の既存の型を再利用するかどうかを指定します。  既定では、このチェック ボックスはオンになっています。  
  
 **\[参照されたアセンブリすべてで型を再利用\]**  
 オンになっている場合、**\[Referenced assemblies list \(参照されたアセンブリ一覧\)\]** 内のすべての型は可能であれば再利用されます。  既定では、このチェック ボックスはオンになっています。  
  
 **\[参照されたアセンブリを指定して型を再利用\]**  
 オンになっている場合、**\[Referenced assemblies list \(参照されたアセンブリ一覧\)\]** 内の選択された型のみが再利用されます。  
  
 **\[Referenced assemblies list \(参照されたアセンブリ一覧\)\]**  
 プロジェクトまたは Web サイトで参照されたアセンブリの一覧を含みます。  **\[参照されたアセンブリを指定して型を再利用\]** がオンになっている場合、個別のアセンブリを選択または選択解除できます。  
  
 **\[Web 参照の追加\]**  
 [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/ja-jp/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)を表示します。  
  
> [!NOTE]
>  このオプションは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョン 2.0 を対象にするプロジェクトでのみ使用する必要があります。  
  
> [!NOTE]
>  **\[Web 参照の追加\]** ボタンは、**\[サービス参照の構成\]** ダイアログ ボックスが [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)から表示された場合にのみ使用できます。  
  
## 参照  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)   
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Windows Communication Foundation サービスと WCF データ サービス](../data-tools/configure-service-reference-dialog-box.md)   
 [ASMX サービスと WCF サービスを利用するサンプル](http://msdn.microsoft.com/ja-jp/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)
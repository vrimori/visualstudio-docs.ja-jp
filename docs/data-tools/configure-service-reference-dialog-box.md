---
title: "サービス参照 ダイアログ ボックスの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0826d241cc1f3741a35e635bc27dff1d69ad86af
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="configure-service-reference-dialog-box"></a>[サービス参照の構成] ダイアログ ボックス
**サービス参照の構成**ダイアログ ボックスでは、動作を構成できます。 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] services です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 アクセスする、**サービス参照の構成**でサービスを右クリックしてダイアログ ボックスを参照**ソリューション エクスプ ローラー**選択**サービス参照の構成**です。 ダイアログ ボックスをクリックしてアクセスすることもできます、**詳細**ボタンをクリックして、**サービス参照の追加 ダイアログ ボックス**です。  
  
## <a name="task-list"></a>タスク一覧  
  
-   WCF サービスがホストされているアドレスを変更するで新しいアドレスを入力、**アドレス**フィールドです。  
  
-   WCF クライアント クラスのアクセス レベルを変更するでのアクセス レベル キーワードを選択、**アクセス レベルが生成されたクラスの** ボックスの一覧です。  
  
-   WCF サービスのメソッドを非同期に呼び出すには、選択、**非同期操作を生成する**チェック ボックスをオンします。  
  
-   WCF クライアントでは、メッセージ コントラクト型を生成するには、選択、**メッセージ コントラクトを常に生成**チェック ボックスをオンします。  
  
-   WCF クライアントのリストまたはディクショナリ コレクションの型を指定するにからの種類を選択、**コレクション型**と**ディクショナリ コレクション型**を一覧表示します。  
  
-   型の共有を無効にする、オフ、**参照されたアセンブリで型を再利用**チェック ボックスをオンします。 型の参照先アセンブリのサブセットの共有を有効にするを選択して、**参照されたアセンブリで型を再利用**チェック ボックスで、**指定された参照されたアセンブリで型を再利用**、し、目的は、参照、**参照されたアセンブリ一覧**です。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **アドレス**  
 サービス参照がサービスを検索する Web アドレスを更新するために使用されます。 たとえば、開発中のサービスは開発サーバーでホストされ、その後、運用サーバーに移されることがあり、アドレスの変更が必要になります。  
  
> [!NOTE]
>  Address 要素は使用可能な場合に、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**です。  
  
 **生成されたクラスのアクセス レベル**  
 WCF クライアント クラスのコード アクセス レベルを特定します。  
  
> [!NOTE]
>  Web サイト プロジェクトの場合、このオプションは常に `Public` に設定され、変更できません。 詳細については、次を参照してください。[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)です。  
  
 **非同期操作を生成します。**  
 WCF サービス メソッドの呼び出しが同期 (既定) または非同期のどちらであるかを指定します。  
  
 **タスク ベースの操作を生成します。**  
 非同期コードを作成する場合、このオプションにより、.Net 4 で導入されたタスク並列ライブラリ (TPL) を利用できます。 参照してください[タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)です。  
  
 **常にメッセージ コントラクトを生成します。**  
 WCF クライアント向けにメッセージ コントラクト型が生成されるかどうかを指定します。 メッセージ コントラクトの詳細については、次を参照してください。[メッセージ コントラクトを使用して](/dotnet/framework/wcf/feature-details/using-message-contracts)です。  
  
 **コレクション型**  
 WCF クライアントのリスト コレクション型を指定します。 既定の型は <xref:System.Array> です。  
  
 **ディクショナリ コレクション型**  
 WCF クライアントのディクショナリ コレクション型を指定します。 既定の型は <xref:System.Collections.Generic.Dictionary%602> です。  
  
 **参照されたアセンブリで型を再利用します。**  
 サービスが追加または更新された場合、WCF クライアントが、新しい型を生成する代わりに、参照されたアセンブリ内の既存の型を再利用するかどうかを指定します。 既定では、このチェック ボックスはオンになっています。  
  
 **すべての参照されたアセンブリで型を再利用します。**  
 選択した場合、すべての型、**参照されたアセンブリ一覧**可能であれば再利用されます。 既定では、このチェック ボックスはオンになっています。  
  
 **指定した参照されたアセンブリで型を再利用します。**  
 選択した場合、選択された型でのみ、**参照されたアセンブリ一覧**が再利用されます。  
  
 **参照先アセンブリの一覧**  
 プロジェクトまたは Web サイトで参照されたアセンブリの一覧を含みます。 ときに**指定された参照されたアセンブリで型を再利用**が選択されている個別のアセンブリを選択またはクリアします。  
  
 **Web 参照を追加します。**  
 表示、 [Web 参照 ダイアログ ボックスを追加](https://msdn.microsoft.com/en-us/library/8dcbc50t(v=vs.100).aspx)です。  
  
> [!NOTE]
>  このオプションは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョン 2.0 を対象にするプロジェクトでのみ使用する必要があります。  
  
> [!NOTE]
>  **Web 参照の追加**ボタンは使用可能な場合にのみ、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**です。  
  
## <a name="see-also"></a>関連項目  

 [方法: Web サービスへの参照を追加](how-to-add-update-or-remove-a-wcf-data-service-reference.md)   
 [Windows Communication Foundation サービスと WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
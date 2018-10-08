---
title: サービス参照 ダイアログ ボックスの構成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 60a1c7a057495b89aa8923d424fb09d9ecb1c232
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536416"
---
# <a name="configure-service-reference-dialog-box"></a>[サービス参照の構成] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サービス参照の構成 ダイアログ ボックス](https://docs.microsoft.com/visualstudio/data-tools/configure-service-reference-dialog-box)します。  
  
  
**サービス参照の構成**ダイアログ ボックスでは、動作を構成できます。[!INCLUDE[vsindigo](../includes/vsindigo-md.md)]サービス。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 アクセスする、**サービス参照の構成**でダイアログ ボックスで、右クリックして、サービスが参照**ソリューション エクスプ ローラー**選択**サービス参照の構成**します。 ダイアログ ボックスをクリックしてアクセスすることもできます、**詳細**ボタン、**サービス参照の追加 ダイアログ ボックス**します。  
  
## <a name="task-list"></a>タスク一覧  
  
-   WCF サービスがホストされているアドレスを変更するには、新しいアドレスを入力、**アドレス**フィールド。  
  
-   WCF クライアント クラスのアクセス レベルを変更するアクセス レベル キーワードを選択します。、**アクセス レベルが生成されたクラスの**一覧。  
  
-   WCF サービスのメソッドを非同期的に呼び出すには、選択、**非同期操作を生成する**チェック ボックスをオンします。  
  
-   WCF クライアントでは、メッセージ コントラクト型を生成するには、選択、**メッセージ コントラクトを常に生成**チェック ボックスをオンします。  
  
-   WCF クライアントのリストまたはディクショナリ コレクションの種類を指定するからの種類を選択、**コレクション型**と**ディクショナリ コレクション型**を一覧表示します。  
  
-   型の共有を無効にするのには、オフ、**参照されたアセンブリで型を再利用**チェック ボックスをオンします。 型の参照先アセンブリのサブセットの共有を有効にするのには、選択、**参照されたアセンブリで型を再利用**チェック ボックスをオン**参照されたアセンブリを指定した型を再利用**、目的を選択します内の参照、**参照されたアセンブリ一覧**します。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **アドレス**  
 サービス参照がサービスを検索する Web アドレスを更新するために使用されます。 たとえば、開発中のサービスは開発サーバーでホストされ、その後、運用サーバーに移されることがあり、アドレスの変更が必要になります。  
  
> [!NOTE]
>  場合、Address 要素は使用できません、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**します。  
  
 **生成されたクラスのアクセス レベル**  
 WCF クライアント クラスのコード アクセス レベルを特定します。  
  
> [!NOTE]
>  Web サイト プロジェクトの場合、このオプションは常に `Public` に設定され、変更できません。 詳細については、次を参照してください。[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)します。  
  
 **非同期操作を生成します。**  
 WCF サービス メソッドの呼び出しが同期 (既定) または非同期のどちらであるかを指定します。  
  
 **タスク ベースの操作を生成します。**  
 非同期コードを作成する場合、このオプションにより、.Net 4 で導入されたタスク並列ライブラリ (TPL) を利用できます。 参照してください[タスク並列ライブラリ (TPL)](http://msdn.microsoft.com/library/dd460717.aspx)します。  
  
 **メッセージ コントラクトを常に生成します。**  
 WCF クライアント向けにメッセージ コントラクト型が生成されるかどうかを指定します。 メッセージ コントラクトの詳細については、次を参照してください。 [Using Message Contracts](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249)します。  
  
 **コレクション型**  
 WCF クライアントのリスト コレクション型を指定します。 既定の型は <xref:System.Array> です。  
  
 **ディクショナリ コレクション型**  
 WCF クライアントのディクショナリ コレクション型を指定します。 既定の型は <xref:System.Collections.Generic.Dictionary%602> です。  
  
 **参照されたアセンブリで型を再利用します。**  
 サービスが追加または更新された場合、WCF クライアントが、新しい型を生成する代わりに、参照されたアセンブリ内の既存の型を再利用するかどうかを指定します。 既定では、このチェック ボックスはオンになっています。  
  
 **参照されたアセンブリすべてで型を再利用します。**  
 選択した場合、すべての型、**参照されたアセンブリ一覧**可能であれば再利用されます。 既定では、このチェック ボックスはオンになっています。  
  
 **指定した参照されたアセンブリで型を再利用します。**  
 選択した場合、選択した型でのみ、**参照されたアセンブリ一覧**が再利用されます。  
  
 **参照先アセンブリの一覧**  
 プロジェクトまたは Web サイトで参照されたアセンブリの一覧を含みます。 ときに**参照されたアセンブリを指定した型を再利用**が選択されている個々 のアセンブリを選択またはクリアできます。  
  
 **Web 参照を追加します。**  
 表示、 [NIB: Web 参照 ダイアログ ボックスを追加](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)します。  
  
> [!NOTE]
>  このオプションは、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] のバージョン 2.0 を対象にするプロジェクトでのみ使用する必要があります。  
  
> [!NOTE]
>  **Web 参照の追加**ボタンが使用可能な場合にのみ、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**します。  
  
## <a name="see-also"></a>関連項目  
 [方法: 追加、更新、またはサービス参照の削除](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [方法: Web サービスへの参照の追加](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Windows Communication Foundation サービスと WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)


---
title: '[サービス参照の構成] ダイアログ ボックス'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: daa18ea2716972daa1429580ad0b2f5be5afe76c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854079"
---
# <a name="configure-service-reference-dialog-box"></a>[サービス参照の構成] ダイアログ ボックス

**サービス参照の構成** ダイアログ ボックスでは、Windows Communication Foundation (WCF) サービスの動作を構成することができます。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

アクセスする、**サービス参照の構成**でダイアログ ボックスで、右クリックして、サービスが参照**ソリューション エクスプ ローラー**選択**サービス参照の構成**します。 ダイアログ ボックスをクリックしてアクセスすることもできます、**詳細**ボタン、**サービス参照の追加 ダイアログ ボックス**します。

## <a name="task-list"></a>タスク一覧

- WCF サービスがホストされているアドレスを変更するには、新しいアドレスを入力、**アドレス**フィールド。

- WCF クライアント クラスのアクセス レベルを変更するアクセス レベル キーワードを選択します。、**アクセス レベルが生成されたクラスの**一覧。

- WCF サービスのメソッドを非同期的に呼び出すには、選択、**非同期操作を生成する**チェック ボックスをオンします。

- WCF クライアントでは、メッセージ コントラクト型を生成するには、選択、**メッセージ コントラクトを常に生成**チェック ボックスをオンします。

- WCF クライアントのリストまたはディクショナリ コレクションの種類を指定するからの種類を選択、**コレクション型**と**ディクショナリ コレクション型**を一覧表示します。

- 型の共有を無効にするのには、オフ、**参照されたアセンブリで型を再利用**チェック ボックスをオンします。 型の参照先アセンブリのサブセットの共有を有効にするのには、選択、**参照されたアセンブリで型を再利用**チェック ボックスをオン**参照されたアセンブリを指定した型を再利用**、目的を選択します内の参照、**参照されたアセンブリ一覧**します。

## <a name="uielement-list"></a>UIElement の一覧

 **アドレス**

 サービス参照がサービスを検索する web アドレスを更新します。 たとえば、開発中は、サービスを開発サーバーでホストされているし、し、後で、アドレスの変更を加えなくて、実稼働サーバーに移動する可能性があります。

> [!NOTE]
> 場合、Address 要素は使用できません、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**します。

 **生成されたクラスのアクセス レベル**

 WCF クライアント クラスのコード アクセス レベルを特定します。

> [!NOTE]
> Web サイト プロジェクトの場合、このオプションは常に `Public` に設定され、変更できません。 詳細については、次を参照してください。[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)します。

 **非同期操作を生成します。**

 WCF サービスのメソッドが同期的に呼び出されるかどうかを決定します (既定値) または非同期的にします。

 **タスク ベースの操作を生成します。**

 非同期コードを記述するときのタスク並列ライブラリ (TPL) 導入された .NET 4 を利用するこのオプションを使用できます。 参照してください[タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)します。

 **メッセージ コントラクトを常に生成します。**

 WCF クライアントのメッセージ コントラクト型を生成するかどうかを判断します。 メッセージ コントラクトの詳細については、次を参照してください。[メッセージ コントラクトを使用して](/dotnet/framework/wcf/feature-details/using-message-contracts)します。

 **コレクション型**

 WCF クライアントのリスト コレクション型を指定します。 既定の型は <xref:System.Array> です。

 **ディクショナリ コレクション型**

 WCF クライアントのディクショナリ コレクション型を指定します。 既定の型は <xref:System.Collections.Generic.Dictionary%602> です。

 **参照されたアセンブリで型を再利用します。**

 WCF クライアントがサービスを追加または更新時に、新しい型を生成する代わりに参照されたアセンブリ内に既に存在する再利用しようとしたかどうかを判断します。 既定では、このチェック ボックスはオンになっています。

 **参照されたアセンブリすべてで型を再利用します。**

 選択した場合、すべての型、**参照されたアセンブリ一覧**可能であれば再利用されます。 既定では、このチェック ボックスはオンになっています。

 **指定した参照されたアセンブリで型を再利用します。**

 選択した場合、選択した型でのみ、**参照されたアセンブリ一覧**は再利用されます。

 **参照先アセンブリの一覧**

 プロジェクトまたは web サイトの参照先アセンブリの一覧が含まれています。 選択すると**参照されたアセンブリを指定した型を再利用**を選択または個々 のアセンブリをオフにすることができます。

 **Web 参照を追加します。**

 表示、 **Web 参照の追加** ダイアログ ボックス。

> [!NOTE]
> このオプションは、プロジェクトのバージョン 2.0 をターゲットにのみ使用する必要があります、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]します。
> 
> [!NOTE]
> **Web 参照の追加**ときにボタンが使用可能なだけ、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**します。

## <a name="see-also"></a>関連項目

- [方法: web サービスへの参照の追加](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation サービスと WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
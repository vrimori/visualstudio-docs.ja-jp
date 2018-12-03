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
ms.openlocfilehash: f0cb2737356813a9b637d7f16e9d5cda704c022a
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389501"
---
# <a name="configure-service-reference-dialog-box"></a>[サービス参照の構成] ダイアログ ボックス

**サービス参照の構成** ダイアログ ボックスでは、Windows Communication Foundation (WCF) サービスの動作を構成することができます。

**[サービス参照の構成]** ダイアログ ボックスにアクセスするには、**ソリューション エクスプローラー**でサービス参照を右クリックし、**[サービス参照の構成]** を選択します。 **[サービス参照の追加] ダイアログ ボックス**で **[詳細]** ボタンをクリックしてダイアログ ボックスにアクセスすることもできます。

## <a name="task-list"></a>タスク一覧

- WCF サービスがホストされるアドレスを変更するには、**[アドレス]** フィールドに新しいアドレスを入力します。

- WCF クライアント内のクラスのアクセス レベルを変更するには、**[生成されたクラスのアクセス レベル]** リストでアクセス レベル キーワードを選択します。

- WCF サービスのメソッドを非同期に呼び出すには、**[非同期操作を生成する]** チェック ボックスをオンにします。

- WCF クライアントでメッセージ コントラクト型を生成するには、**[メッセージ コントラクトを常に生成]** チェック ボックスをオンにします。

- WCF クライアントのリストまたはディクショナリ コレクションの型を指定するには、**[コレクション型]** リストおよび **[ディクショナリ コレクション型]** リストから型を選択します。

- 型の共有を無効にするには、**[参照されたアセンブリで型を再利用]** チェック ボックスをオフにします。 参照されたアセンブリのサブセットで型の共有を有効にするには、**[参照されたアセンブリで型を再利用]** チェック ボックスをオンにし、**[参照されたアセンブリを指定して型を再利用]** チェック ボックスをオンにして、**[Referenced assemblies list]\(参照されたアセンブリの一覧\)** で必要な参照を選択します。

## <a name="uielement-list"></a>UIElement の一覧

 **Address**

 サービス参照がサービスを検索する web アドレスを更新します。 たとえば、開発中は、サービスを開発サーバーでホストされているし、し、後で、アドレスの変更を加えなくて、実稼働サーバーに移動する可能性があります。

> [!NOTE]
> Address 要素は、**[サービス参照の構成]** ダイアログ ボックスが **[サービス参照の追加] ダイアログ ボックス**から表示された場合は使用できません。

 **[生成されたクラスのアクセス レベル]**

 WCF クライアント クラスのコード アクセス レベルを特定します。

> [!NOTE]
> Web サイト プロジェクトの場合、このオプションは常に `Public` に設定され、変更できません。 詳細については、「[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)」を参照してください。

 **[非同期操作を生成する]**

 WCF サービスのメソッドが同期的に呼び出されるかどうかを決定します (既定値) または非同期的にします。

 **[タスク ベースの操作を生成する]**

 非同期コードを記述するときのタスク並列ライブラリ (TPL) 導入された .NET 4 を利用するこのオプションを使用できます。 参照してください[タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)します。

 **[メッセージ コントラクトを常に生成]**

 WCF クライアントのメッセージ コントラクト型を生成するかどうかを判断します。 メッセージ コントラクトの詳細については、「[メッセージ コントラクトの使用](/dotnet/framework/wcf/feature-details/using-message-contracts)」を参照してください。

 **[コレクション型]**

 WCF クライアントのリスト コレクション型を指定します。 既定の型は <xref:System.Array> です。

 **[ディクショナリ コレクション型]**

 WCF クライアントのディクショナリ コレクション型を指定します。 既定の型は <xref:System.Collections.Generic.Dictionary%602> です。

 **[参照されたアセンブリで型を再利用]**

 WCF クライアントがサービスを追加または更新時に、新しい型を生成する代わりに参照されたアセンブリ内に既に存在する再利用しようとしたかどうかを判断します。 既定では、このチェック ボックスはオンになっています。

 **[参照されたアセンブリすべてで型を再利用]**

 選択した場合、すべての型、**参照されたアセンブリ一覧**可能であれば再利用されます。 既定では、このチェック ボックスはオンになっています。

 **[参照されたアセンブリを指定して型を再利用]**

 選択した場合、選択した型でのみ、**参照されたアセンブリ一覧**は再利用されます。

 **[Referenced assemblies list]\(参照されたアセンブリの一覧\)**

 プロジェクトまたは web サイトの参照先アセンブリの一覧が含まれています。 選択すると**参照されたアセンブリを指定した型を再利用**を選択または個々 のアセンブリをオフにすることができます。

 **[Web 参照の追加]**

 **[Web 参照の追加]** ダイアログ ボックスを表示します。

> [!NOTE]
> このオプションは、プロジェクトのバージョン 2.0 をターゲットにのみ使用する必要があります、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]します。
>
> [!NOTE]
> **Web 参照の追加**ときにボタンが使用可能なだけ、**サービス参照の構成**からダイアログ ボックスが表示されます、**サービス参照の追加 ダイアログ ボックス**します。

## <a name="see-also"></a>関連項目

- [方法 : Web サービスへの参照を追加する](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation サービスと WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
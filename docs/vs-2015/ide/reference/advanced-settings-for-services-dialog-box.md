---
title: '[サービスの詳細設定] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea79a5539ad41a4f6e56a6069889e06bc45dde65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535884"
---
# <a name="advanced-settings-for-services-dialog-box"></a>[サービスの詳細設定] ダイアログ ボックス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サービス] ダイアログ ボックスの [詳細設定](https://docs.microsoft.com/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)します。  
  
  
クライアント アプリケーション サービスにより、Windows フォーム アプリケーションおよび Windows Presentation Foundation (WPF) アプリケーションから [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] ログイン サービス、ロール サービス、プロファイル サービスに簡単にアクセスできます。 **プロジェクト デザイナー**の **[サービス]** ページを使用して、クライアント アプリケーション サービスを構成することができます。 **[サービス]** ページの詳細については、「[Services Page, Project Designer](../../ide/reference/services-page-project-designer.md)」([サービス] ページ (プロジェクト デザイナー)) を参照してください。  
  
 **プロジェクト デザイナー**の **[サービスの詳細設定]** ダイアログ ボックスの **[サービス]** ページを使用して、クライアント アプリケーション サービスの詳細設定を構成します。 これらの設定を使用すると、既定のアプリケーション サービスの動作の一部をオーバーライドして、あまり一般的ではないシナリオに対応することができます。 詳細については、「[クライアント アプリケーション サービス](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)」を参照してください。  
  
 **[サービスの詳細設定]** ダイアログ ボックスにアクセスするには、**ソリューション エクスプローラー**でプロジェクト ノードを選択し、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。 **プロジェクト デザイナー**が表示されたら、**[サービス]** タブをクリックし、**[詳細設定]** ボタンをクリックします。 クライアント アプリケーション サービスを有効にするまで、このボタンは無効です。  
  
## <a name="task-list"></a>タスク一覧  
 [方法 : クライアント アプリケーション サービスを構成する](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [方法 : クライアント アプリケーション サービスをオフライン モードで操作する](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **オフラインでログインできるようにパスワードのハッシュをローカルに保存する**  
 暗号化された形式のユーザー パスワードをローカルにキャッシュして、アプリケーションがオフライン モードのときでもユーザーがログインできるようにするかどうかを指定します。 詳細については、「[How to: Work Offline with Client Application Services](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)」(方法: クライアント アプリケーション サービスをオフライン モードで操作する) を参照してください。 既定では、このオプションはオンです。  
  
 **サーバー クッキーの期限が切れた場合は常に再度ログオンすることをユーザーに要求する**  
 アプリケーションがロールまたはプロファイル サービスにアクセスし、サーバー認証の Cookie が期限切れになっているときに、以前に認証済みのユーザーを自動的に再認証するかどうかを指定します。 Cookie の期限切れ後はアプリケーション サービスへのアクセスを拒否し、明示的に再認証を必須にするには、このオプションをオンにします。 このオプションは、公共の場所に配置されたアプリケーションで、使用後にアプリケーションを実行中のままにしているユーザーが無期限に認証されないようにするのに便利です。 既定では、このオプションはオフになっています。  
  
 **ロール サービスのキャッシュのタイムアウト**  
 クライアント ロール プロバイダーが、ロール サービスにアクセスせずにキャッシュ済みのロール値を使用する時間を指定します。 この時間間隔は、ロールが頻繁に更新される場合は小さい値に設定し、ロールが頻繁に更新されない場合はより大きい値に設定します。 既定値は 1 日です。  
  
 <xref:System.Web.Security.RolePrincipal.IsInRole%2A> メソッドを呼び出すと、ロール プロバイダーがキャッシュされたロール値またはロール サービスにアクセスします。 プログラムによってキャッシュを消去し、強制的にこのメソッドがリモート サービスにアクセスするようにするには、<xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> メソッドを呼び出します。  
  
 **カスタム接続文字列を使用**  
 クライアント サービス プロバイダーがローカル キャッシュにカスタムのデータ ストアを使用するかどうかを指定します。 既定では、サービス プロバイダーはキャッシュのローカル ファイル システムを使用します。 このオプションをオンにすると、テキスト ボックスには既定の接続文字列が自動的に入力されます。 自動生成される既定の接続文字列のままにして、SQL Server Compact Edition データベースを使用するか、既存の SQL Server データベースに対する接続文字列を指定することができます。 詳細については、「 [How to: Configure Client Application Services](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)」を参照してください。 既定では、このオプションはオフになっています。  
  
## <a name="see-also"></a>関連項目  
 [クライアント アプリケーション サービス](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [[サービス] ページ (プロジェクト デザイナー)](../../ide/reference/services-page-project-designer.md)   
 [方法 : クライアント アプリケーション サービスを構成する](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [方法 : クライアント アプリケーション サービスをオフライン モードで操作する](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)




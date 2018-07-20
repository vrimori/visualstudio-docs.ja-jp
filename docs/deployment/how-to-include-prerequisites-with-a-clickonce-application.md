---
title: '方法: ClickOnce アプリケーションと共に必須コンポーネントを含める |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f961229e60cb291efdd7630f9df10e162c2f17b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153843"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>方法: ClickOnce アプリケーションと共に必須コンポーネントが含まれます
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションと共に必須コンポーネントを配布する前に、まず開発用コンピューターにそれらの必須コンポーネントのインストーラー パッケージをダウンロードする必要があります。 アプリケーションを発行し、選択**アプリケーションと同じ場所から必須コンポーネントをダウンロード**、インストーラー パッケージがない場合、エラーが発生、**パッケージ**フォルダー。  
  
> [!NOTE]
>  .NET Framework のインストーラー パッケージを追加するを参照してください。[開発者向けの .NET Framework 配置ガイド](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx)します。  
  
##  <a name="Package"></a> Package.xml を使用してインストーラー パッケージを追加するには  
  
1.  ファイル エクスプ ローラーで開き、**パッケージ**フォルダー。  
  
     既定では、パスは*C:\Program files \microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* 32 ビット システム上と*C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* 64 ビット システムでします。  
  
2.  を追加するための前提条件のフォルダーを開き、インストールされているバージョンの言語フォルダーを開きます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)](たとえば、 **en**英語の場合)。  
  
3.  メモ帳で開き、 *Package.xml*ファイル。  
  
4.  検索、**名前**要素を含む**http://go.microsoft.com/fwlink**URL をコピーします。 含める、 **LinkID**部分。  
  
    > [!NOTE]
    >  ない場合は**名前**要素が含まれます**http://go.microsoft.com/fwlink**、オープン、 **Product.xml**ファイル、前提条件のルート フォルダーを探し、 **fwlink**文字列。  
  
    > [!IMPORTANT]
    >  一部の必須コンポーネントには、複数のインストーラー パッケージ (たとえば、32 ビット システム用または 64 ビット システム用) があります。 複数**名前**要素が含まれる**fwlink**、それぞれの残りの手順を繰り返す必要があります。  
  
5.  ブラウザーのアドレス バーに URL を貼り付けるし、実行または保存を求められたらを選択し、**保存**します。  
  
     この手順では、コンピューターにインストーラー ファイルをダウンロードします。  
  
6.  必須コンポーネントのルート フォルダーにファイルをコピーします。  
  
     たとえば、Windows インストーラー 4.5 の前提条件のファイルのコピー、 *\Packages\WindowsInstaller4_5*フォルダー。  
  
     これで、アプリケーションと共にインストーラー パッケージを配布できます。  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションの前提条件のインストール](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
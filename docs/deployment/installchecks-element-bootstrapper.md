---
title: '&lt;InstallChecks&gt;要素 (ブートス トラップ) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcfd8aaa0048cac3fb9a33c7974132655de87a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566174"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt;要素 (ブートス トラップ)
`InstallChecks`要素は、さまざまなすべてのアプリケーションの適切な前提条件がインストールされているかどうかを確認するローカル コンピューターに対するテストの開始をサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 この要素の省略可能な子要素である`InstallChecks`です。 インスタンスごとに`AssemblyCheck`、ブートス トラップが要素で指定されたアセンブリがグローバル アセンブリ キャッシュ (GAC) に存在することを確認してください。 これは、要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
|`Name`|必須。 チェック対象のアセンブリの完全修飾名。|  
|`PublicKeyToken`|必須。 公開キーの省略形は、このアセンブリの厳密な名前に関連付けられています。 GAC に格納されているすべてのアセンブリは、名前、バージョン、および公開キーが必要です。|  
|`Version`|必須。 アセンブリのバージョン。<br /><br /> バージョン番号が、形式\<*メジャー バージョン*>.\<*マイナー バージョン*>.\<*ビルド バージョン*>.\<*リビジョン バージョン*>。|  
|`Language`|任意。 ローカライズされたアセンブリの言語です。 既定値は `neutral` です。|  
|`ProcessorArchitecture`|任意。 このインストールの対象となるコンピューターのプロセッサ。 既定値は `msil` です。|  
  
## <a name="externalcheck"></a>ExternalCheck  
 この要素の省略可能な子要素である`InstallChecks`です。 インスタンスごとに`ExternalCheck`、ブートス トラップが別のプロセスで指定された外部プログラムを実行し、その終了コードによって示されるプロパティに格納`Property`です。 `ExternalCheck` 複雑な依存関係のチェックを実装するため、またはコンポーネントの有無を確認する唯一の方法はそれをインスタンス化するときに便利です。  
  
 `ExternalCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
|`PackageFile`|必須。 実行する外部プログラムです。 プログラムは、セットアップの配布パッケージの一部である必要があります。|  
|`Arguments`|任意。 によって指定された実行可能ファイルにコマンドライン引数を指定`PackageFile`です。|  
  
## <a name="filecheck"></a>チェックイン  
 この要素の省略可能な子要素である`InstallChecks`です。 インスタンスごとに`FileCheck`、ブートス トラップは、名前付きのファイルが存在し、ファイルのバージョン番号を返すかどうかが決まります。 ブートス トラップがで指定したプロパティを設定、ファイルがバージョン番号を持たない場合`Property`を 0 にします。 ファイルが存在しない場合`Property`任意の値に設定されていません。  
  
 `FileCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
|`FileName`|必須。 検索するファイルの名前です。|  
|`SearchPath`|必須。 ディスクまたはファイルを検索するフォルダーです。 これは、場合は相対パスにする必要があります`SpecialFolder`が割り当てられます。 それ以外の場合、その絶対パスである必要があります。|  
|`SpecialFolder`|任意。 Windows をまたはに特別な意味を持つフォルダーを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]です。 既定では、解釈`SearchPath`に絶対パス。 以下の値が有効です。<br /><br /> `AppDataFolder`。 このアプリケーション データ フォルダー[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション; 現在のユーザーを特定します。<br /><br /> `CommonAppDataFolder`。 すべてのユーザーによって使用されるアプリケーション データ フォルダーです。<br /><br /> `CommonFilesFolder`。 現在のユーザーの一般的なファイル フォルダーです。<br /><br /> `LocalDataAppFolder`。 非ローミングのアプリケーション データ フォルダーです。<br /><br /> `ProgramFilesFolder`。 32 ビット アプリケーションの標準の Program Files フォルダーです。<br /><br /> `StartUpFolder`。 このフォルダーは、システムの起動時に起動されたすべてのアプリケーションが含まれています。<br /><br /> `SystemFolder`。 このフォルダーは、32 ビット システム Dll が含まれています。<br /><br /> `WindowsFolder`。 Windows システムのインストールに含まれているフォルダーです。<br /><br /> `WindowsVolume`。 ドライブまたはパーティションを Windows システムのインストールが含まれています。|  
|`SearchDepth`|任意。 指定されたファイル用のサブフォルダーを検索する位置の深さです。 検索では、深さ優先します。 既定値は 0 で、最上位フォルダーで指定された検索範囲を限定`SpecialFolder`と**代替**です。|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 この要素の省略可能な子要素である`InstallChecks`です。 インスタンスごとに`MsiProductCheck`、ブートス トラップが完了するまでに指定した Microsoft Windows インストーラーのインストールが実行するかどうかを確認します。 プロパティの値は、製品のインストールの状態に応じて設定されます。 正の値は、製品がインストールされていることを示します 0 または-1 は、インストールされていないことを示します。 (詳細については、Windows インストーラー SDK 関数 MsiQueryFeatureState 参照してください。 してください。). Windows インストーラーが、コンピューターにインストールされていない場合`Property`が設定されていません。  
  
 `MsiProductCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
|`Product`|必須。 インストールされている製品の GUID です。|  
|`Feature`|任意。 インストールされているアプリケーションの特定の機能の GUID です。|  
  
## <a name="registrycheck"></a>RegistryCheck  
 この要素の省略可能な子要素である`InstallChecks`です。 インスタンスごとに`RegistryCheck`、ブートス トラップが指定されたレジストリ キーが存在するかどうか、指定された値があるかどうかを確認します。  
  
 `RegistryCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
|`Key`|必須。 レジストリ キーの名前。|  
|`Value`|任意。 取得するレジストリ値の名前。 既定では、既定値のテキストを返します。 `Value` 文字列または DWORD のいずれかにする必要があります。|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 この要素の省略可能な子要素である`InstallChecks`です。 インスタンスごとに`RegistryFileCheck`、ブートス トラップは指定されたレジストリ キーからファイルへのパスを取得しようとして最初に、指定されたファイルのバージョンを取得します。 これは、レジストリの値として指定されたディレクトリにファイルを検索する場合に特に便利です。  
  
 `RegistryFileCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
|`Key`|必須。 レジストリ キーの名前。 しない限り、その値は、ファイルへのパスとして解釈されます、`File`属性を設定します。 このキーが存在しない場合`Property`が設定されていません。|  
|`Value`|任意。 取得するレジストリ値の名前。 既定では、既定値のテキストを返します。 `Value` 文字列である必要があります。|  
|`FileName`|任意。 ファイルの名前。 指定すると、レジストリ キーから得られた値と見なされます、ディレクトリ パスを指定してにこの名前が追加されます。 指定しない場合、レジストリから返される値は、ファイルへの完全パスと見なされます。|  
|`SearchDepth`|任意。 指定されたファイル用のサブフォルダーを検索する位置の深さです。 検索では、深さ優先します。 既定値は、0 で、レジストリ キーの値で指定された最上位のフォルダーへの検索を制限します。|  
  
## <a name="remarks"></a>コメント  
 下にある要素を while`InstallChecks`実行するテストを定義し、それらは実行されません。 テストを実行する必要がありますを作成する`Command`要素の下に、`Commands`要素。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`InstallChecks`の製品ファイルと要素が使用される、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 ときに`InstallChecks`はそれらが評価される、プロパティを生成します。 プロパティを使用し、`InstallConditions`かを特定するパッケージする必要がありますをインストール、バイパス、失敗します。 次の表、 `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|存在する場合`FailIf`条件が true に評価されると、パッケージは失敗します。 残りの条件は評価されません。|  
|`BypassIf`|存在する場合`BypassIf`条件が true に評価された、パッケージがバイパスされます。 残りの条件は評価されません。|  
  
## <a name="predefined-properties"></a>定義済みのプロパティ  
 次の表、`BypassIf`と`FailIf`要素。  
  
|プロパティ|メモ|使用できる値|  
|--------------|-----------|---------------------|  
|`Version9X`|Windows 9x X オペレーティング システムのバージョン番号。|4.10 Windows 98 を =|  
|`VersionNT`|Windows NT ベースのオペレーティング システムのバージョン番号。|Major.minor.servicepack です。<br /><br /> 5.0 Windows 2000 を =<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|64 ビット Windows NT ベースのオペレーティング システムのバージョン番号。|上記と同じです。|  
|`VersionMsi`|Windows インストーラー サービスのバージョン番号。|2.0 Windows インストーラー 2.0 を =|  
|`AdminUser`|ユーザーが Windows NT ベースのオペレーティング システムの管理者特権を持つかどうかを指定します。|0 = 管理者特権なし<br /><br /> 1 = 管理者権限|  
  
 たとえば、Windows 95 を実行するコンピューターにインストールをブロックするには、次のようなコードを使用します。  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>関連項目  
 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)
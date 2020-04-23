---
title: CMTrace
titleSuffix: Configuration Manager
description: CMTrace ツールを使用して、Configuration Manager のログ ファイルを表示する方法について説明します。
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-core
ms.topic: conceptual
ms.assetid: 6a4a3290-5228-4871-918a-554aa1c20834
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 8c9c42dcd1e6a6a4ca064953f0513157f5ebb228
ms.sourcegitcommit: bbf820c35414bf2cba356f30fe047c1a34c5384d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81707900"
---
# <a name="cmtrace"></a>CMTrace

*適用対象:Configuration Manager (Current Branch)*

CMTrace は、[Configuration Manager ツール](tools.md)の 1 つです。 次の種類を含む、ログ ファイルを表示および監視することができます。  

- Configuration Manager またはクライアント コンポーネント マネージャー (CCM) 形式のログ ファイル  

- Windows インストーラー ログなどの、ASCII または Unicode のプレーン テキスト ファイル  

ツールは強調表示、フィルター処理、エラー参照を行ってログ ファイルを分析するのに役立ちます。

バージョン 1806 以降では、CMTrace ログ表示ツールが Configuration Manager クライアントと共に自動的にインストールされます。 このツールは、クライアント インストール ディレクトリ (既定では、`%WinDir%\CCM\CMTrace.exe`) に追加されます。<!--1357971-->

> [!Note]  
> .log ファイル拡張子を開くために、CMTrace が Windows で自動登録されることはありません。 詳細については、「[File associations](#file-associations)」 (ファイルの関連付け) を参照してください。  

バージョン 1906 以降、**OneTrace** は、サポート センターの新しいログ ビューアーです。 CMTrace と同様に機能しますが、いくつかの点が改善されています。 詳しくは、「[サポート センターの OneTrace](support-center-onetrace.md)」をご覧ください。

## <a name="usage"></a>使用方法

**CMTrace.exe** を実行します。 初めてツールを実行するときに、ファイルの関連付けに関するプロンプトが表示されます。 詳細については、「[File associations](#file-associations)」 (ファイルの関連付け) を参照してください。

CMTrace でのほとんどのアクションは次のメニューから行います。

- [File](#file-menu)
- [ツール](#tools-menu)

### <a name="file-menu"></a>[ファイル] メニュー

**[ファイル]** メニューでは、次のアクションを利用できます。  

- [開く](#open)
- [Open on Server (サーバーで開く)](#open-on-server)
- [印刷](#print)
- [設定](#preferences)

[ファイル] メニューには、最近使った 8 個のファイルも一覧表示されます。 [ファイル] メニューから、これらのログのいずれかを再度すばやく開くことができます。

#### <a name="open"></a>オープン

ログ ファイルを参照するための [開く] ダイアログ ボックスが表示されます。

次の種類のファイルについて、ビューをフィルター処理します。

- ログ ファイル (\*.log)  
- 古いログ ファイル (\*.lo_)
- すべてのファイル (\*.\*)

既定では、次の 2 つのオプションは選択されません。  

- **[Ignore existing lines]\(既存の行を無視する\)** :これを選択した場合、CMTrace では、選択されたログ ファイルの既存のコンテンツが無視され、追加されたときにのみ新しい行が表示されます。 ログ ファイルのすべての履歴が必要でないときに新しいアクションのみを監視するには、このオプションを使用します。  

- **[Merge selected files]\(選択されたファイルをマージする\)** :このオプションを有効にし、複数のログ ファイルを選択した場合、CMTrace によってビューの選択されたログがマージされます。 単一のログ ファイルの場合と同様に表示されます。 マージされたログは同じように更新され、単一のログ ファイルの場合と同様に他のすべての CMTrace 機能がサポートされます。  

#### <a name="open-on-server"></a>Open on Server (サーバーで開く)

標準的な [参照] ダイアログ ボックスを使用して、サイト システム コンピューター上の Configuration Manager ログ フォルダーを参照します。 ネットワークでリモート コンピューターを参照することもできます。

参照するリモート コンピューターを選択すると、CMTrace によって Configuration Manager の共有が確認されます。 Configuration Manager ログ ファイルで共有が見つからない場合は、エラー メッセージが表示されます。  

参照せずに既知のコンピューターに直接接続するには、[開く](#open)アクションを使用します。 次に、UNC 形式を使用してサーバー名を入力して共有します。

#### <a name="print"></a>[印刷]

標準的な Windows の [印刷] ダイアログ ボックスが表示されます。 このアクションでは、現在のログ ファイルがプリンターに送信されます。 CMTrace の設定の [印刷] タブでの設定に従って、出力が書式設定されます。

#### <a name="preferences"></a>設定

CMTrace の設定を構成します。 次のオプションを使用できます。  

- **[全般]** タブ  

    - **Update Interval\(更新間隔\)** :CMTrace によってログ ファイルの変更が確認され、新しい行が読み込まれる頻度が制御されます。 既定では、この値は 500 ミリ秒です。  

    - **強調表示**:選択されたログの行を強調表示するときに、CMTrace で使用される色が設定されます。 既定では、この色は基本的な黄色 (赤:255、緑:255、青:0) です。  

    - **列**:ログ ビューに表示される列と、その表示順序が構成されます。 既定では、ログ テキスト、コンポーネント、日付/時刻、スレッドが表示されます。  

- **[印刷]** タブ  

    - **列**:ログ ファイルの印刷時に使用される列と、その表示順序が構成されます。 既定では、表示されるのと同じ列が印刷されます。  

    - **印刷の向き**:ログ ファイルを印刷するときの既定の印刷の向きが設定されます。 [印刷] ダイアログ ボックスでこの設定をオーバーライドします。 既定では、縦長の向きが使用されます。  

- **[詳細設定]** タブ  

    - **Update Interval\(更新間隔\)** :多くの行を読み込むときに、CMTrace に指定された間隔でログ ビューを更新するよう強制します。 既定では、このオプションは値 0 で無効になります。  

        > [!Note]  
        > 通常は、 **[更新間隔]** を変更しないでください。 大きなログ ファイルを開くのにかかる時間が大幅に長くなる可能性があります。

### <a name="tools-menu"></a>[ツール] メニュー

**[ツール]** メニューでは、次のアクションを利用できます。

- [検索](#find)
- [次を検索](#find-next)
- [クリップボードにコピー](#copy-to-clipboard)
- [強調表示](#highlight)
- [フィルター](#filter)
- [エラー参照](#error-lookup)
- [一時停止](#pause)
- [詳細の表示/非表示](#showhide-details)
- [Show/Hide Info Pane (情報ウィンドウの表示/非表示)](#showhide-info-pane)

#### <a name="find"></a>[検索]

指定されたテキスト文字列について、開いているログ ファイルを検索します。  

#### <a name="find-next"></a>[次を検索]

[検索] ダイアログ ボックスで以前に指定した、次の一致する文字列が検索されます。  

#### <a name="copy-to-clipboard"></a>クリップボードにコピー

プレーン テキストとして選択された行が Windows クリップボードにコピーされます。 Configuration Manager および CCM ログ ファイルを調べる場合、ビューと同じ順序で列がコピーされます。 タブ文字で各列が区切られます。 電子メール メッセージや他のドキュメントにログをコピーするときは、このアクションを使用します。  

#### <a name="highlight"></a>強調表示

CMTrace で各ログ エントリのテキストを検索するために使用される文字列を入力します。 その後、入力した文字列に一致するログ テキストが強調表示されます。  

- 強調表示では、[設定] で指定した色が使用されます。  

- 強調表示をオフにするには、このフィールドから文字列をクリアします。  

- 10 進数または 16 進数を入力した場合、CMTrace によってスレッド列との値の照合が試行されます。 この動作を使用して、やりとりが行われる可能性のある他のスレッドをフィルター処理せずに、単一スレッドの処理を強調表示します。  

- 大文字と小文字を区別して文字列を比較するには、 **[大文字と小文字を区別する]** オプションを有効にします。  

#### <a name="filter"></a>フィルター

指定された条件に基づいて、ログの行を表示または非表示にします。 表示されているかどうかに関係なく、4 つの列のいずれかにフィルターを適用します。 これらの設定は、開いている各ログ ファイルに適用されます。

例:
<!--SCCMDocs issue #603-->

- "the action" または "the group" を含むエントリ テキストで **smsts.log** をフィルター処理します。
- エントリ テキストに "destination" が含まれている **InventoryAgent.log** をフィルター処理します。

#### <a name="error-lookup"></a>エラー参照

10 進数形式または 16 進数形式でエラー コードを入力または貼り付けて、説明を表示します。 考えられるエラー ソースには、Windows、WMI、Winhttp が含まれます。

#### <a name="pause"></a>一時停止

ログの監視を中断または再開します。 次のいくつかのユース ケースが、このアクションを使用する理由として考えられます。  

- CMTrace でのログ ファイル情報の表示が早すぎるとき  

- ログの監視を一時停止したときに、現在のファイルが新しいログにロール オーバーされた場合、CMTrace で表示される情報が失われない  

- ログ ファイルを調べる間、CMTrace での新しいデータの表示を停止するとき  

#### <a name="showhide-details"></a>詳細の表示/非表示

ログ テキスト以外のすべての列を表示または非表示にします。 また、ウィンドウの幅に合わせてログ テキストの列が拡張されます。 低解像度のコンピューター上でログを表示するときに、このアクションを使用します。 より多くのログ テキストが表示されます。  

> [!Note]  
> プレーン テキスト ファイルを表示する場合、詳細は常に空であるため、CMTrace では自動的に非表示になります。  

#### <a name="showhide-info-pane"></a>Show/Hide Info Pane (情報ウィンドウの表示/非表示)

情報ウィンドウを表示または非表示にします。 低解像度のコンピューター上でログを表示するときに、このアクションを使用します。 より多くのログ記録の詳細が表示されます。  


## <a name="log-pane"></a>ログ ウィンドウ

ログ ウィンドウは CMTrace ウィンドウの上部にあります。 ログ ファイルの行が表示されます。

行を選択すると、その行が Windows の選択された配色を使用して、一時的に強調表示されます。

強調表示された行は、 **[ツール]** メニューの **[強調表示]** オプションで定義した条件と一致します。 強調表示では、 **[設定]** で指定する色が使用されます。

CMTrace では、赤色の背景と黄色のテキストの色を使用して、エラーのある行が表示されます。 CCM 形式のログでは、エントリをエラーとして示す明示的な型の値がログ エントリに含まれます。 他のログ形式の場合、CMTrace では、テキスト文字列のマッチング "エラー" について、各エントリの大文字と小文字を区別しない検索が行われます。

黄色の背景を使用して、警告のある行が表示されます。 CCM 形式のログでは、エントリを警告として示す明示的な型の値がログ エントリに含まれます。 他のログ形式の場合、CMTrace では、テキスト文字列のマッチング "警告" について、各エントリの大文字と小文字を区別しない検索が行われます。


## <a name="info-pane"></a>情報ウィンドウ

情報ウィンドウは CMTrace ウィンドウの下部にあります。 このパックには、次の機能があります。

- 現在選択されているログ エントリに関する詳細情報  

- ログ テキストを表示するテキスト ボックス  

- 書式設定されたテキストが読みやすいように、改行文字が表示される  

- ログ ウィンドウに完全に表示されていない長いエントリを読みやすくする  

**[ツール]** メニューの **[Show/Hide Info Pane]\(情報ウィンドウの表示/非表示\)** オプションを使用して、情報ウィンドウを表示または非表示にします。 情報ウィンドウがログ ウィンドウの半分以上を占める場合、CMTrace では自動的に非表示になります。

### <a name="progress-bar"></a>進行状況バー

最初にログ ファイルを開くときに、CMTrace によって情報ウィンドウが進行状況バーで置き換えられます。 この進行状況は、既存のファイルの内容がどれくらい読み込まれているかを示します。 進行状況が 100% に達すると、CMTrace によって進行状況バーが削除され、情報ウィンドウに置き換えられます。 大きなファイルを読み込むときに、この動作により、読み込みにかかる可能性のある時間が示されます。

### <a name="status-bar"></a>ステータス バー

Configuration Manager 形式と CCM 形式のログ ファイルの場合、ステータス バーに、選択されたログ エントリの経過時間が表示されます。 単一のエントリを選択すると、ツールによって、最初のログ エントリから選択されたエントリまでの時間が表示されます。 複数のエントリを選択した場合は、選択された最上位のエントリから選択された最下位のエントリまでの時間が計算されます。 CMTrace では、次のようにこの情報が書式設定されます。

`Elapsed time is <hours>h <minutes>m <seconds>s <milliseconds>ms (<seconds+milliseconds> seconds)`


## <a name="windows-shell-integration"></a>Windows シェルの統合

CMTrace では、[ファイルの関連付け](#file-associations)と[ドラッグ アンド ドロップ](#drag-and-drop)がサポートされます。

### <a name="file-associations"></a>ファイルの関連付け

CMTrace では、それ自体と .log および .lo_ ファイル名拡張子を関連付けることができます。 プログラムでは、起動時にレジストリが確認され、これらのファイル名拡張子と既に関連付けられているかどうかが判断されます。 CMTrace がファイル名拡張子にまだ関連付けられていない場合、ファイル名拡張子を CMTrace に関連付けるように求められます。 **[今後は確認しない]** を選択した場合、CMTrace では、そのコンピューター上で実行されるときは常にこの確認がスキップされます。

### <a name="drag-and-drop"></a>ドラッグ アンド ドロップ

CMTrace では、基本的なドラッグ アンド ドロップ機能がサポートされます。 ログ ファイルを Windows エクスプローラーから CMTrace にドラッグして開きます。


## <a name="other-tips"></a>その他のヒント

### <a name="last-directory-registry-key"></a>最後のディレクトリのレジストリ キー

<!--511280-->
既定では、CMTrace で最後に開いたログの場所が保存されます。 サイト サーバーでは、既定で毎回ログ パスに設定されるため、この動作が役立ちます。

クライアント上で最初に起動するときは、既定で現在の作業ディレクトリに設定されます。 この場所は、CMTrace を保存した場所のパス、または `%userprofile%\Desktop` などのパスの場合があります。

レジストリ キー `HKEY_CURRENT_USER\Software\Microsoft\Trace32` の**最後のディレクトリ**の値によって、この既定の場所が制御されます。 ご利用のクライアント上でこの値を `%windir%\CCM\Logs` に設定した場合、CMTrace の最初の実行時にクライアント ログの場所でファイルが開かれます。


## <a name="see-also"></a>関連項目

- [ログ ファイル](../plan-design/hierarchy/log-files.md)

- [サポート センター ログ ファイル ビューアー](support-center.md#support-center-log-file-viewer)

- [サポート センターの OneTrace](support-center-onetrace.md)
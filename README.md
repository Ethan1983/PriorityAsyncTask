# PriorityAsyncTask
Android Studio Library Module - PriorityAsyncTask

Same as AsyncTask and supports priority when tasks are executed on
com.unlink.lib.priorityasynctask.PriorityAsyncTask#THREAD_POOL_EXECUTOR.
Similar to Android's AsyncTask, THREAD_POOL_EXECUTOR can be used only from Honeycomb.

Concrete implementations can specify priority via getPriority() and this priority is used
only when the tasks are executed on THREAD_POOL_EXECUTOR and not when executed on custom
executors specified via executeOnExecutor(java.util.concurrent.Executor, Object[]).

This can be used only from API 9 as it uses java.util.ArrayDeque introduced from API 9.

Usage:
-----

private class DemoTask extends PriorityAsyncTask<Void, Void, Void> {
	    @Override
	    protected int getPriority() {
        return PRIORITY_LOW;
      }
	    
	    @Override
	    protected void onPreExecute() {
	      ...
	    }

	    @Override
	    protected Void doInBackground( Void... params ) {
	      ...
	    }

	    @Override
	    protected void onPostExecute(Bitmap bitmap) {
	      ...
	    }
	}
	
	DemoTask demoTask = new DemoTask();
	demoTask.executeOnExecutor(PriorityAsyncTask.THREAD_POOL_EXECUTOR);
